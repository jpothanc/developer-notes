# How to use dependency Injection

```bash
pip install injector
```

```python
def setup_dependencies(injector: Injector):
    injector.binder.bind(AppService, to=AppService, scope=singleton)
    injector.binder.bind(MemoryCache, to=MemoryCache, scope=singleton)


async def run():
    await app_service.load_equity_data('disk_cache.json')
    eq = await app_service.get_equity('AAPL')
    print(eq)

if __name__ == '__main__':
    injector = Injector()
    setup_dependencies(injector)
    app_service = injector.get(AppService)
    # Run the async example using asyncio.run
    asyncio.run(run())


class AppService:
    @inject
    def __init__(self, injector: Injector):
        self.memory_cache = injector.get(MemoryCache)

    async def load_equity_data(self, file_path):
        if not os.path.exists(file_path):
            print(f'File {file_path} does not exist')

        with open(file_path, 'r') as file:
            data = json.load(file)
            for item in data:
                await self.memory_cache.set(item['symbol'], item)

    async def get_equity(self, symbol):
        return await self.memory_cache.get(symbol)

```

# Logging

```python
def init_logging():
    logging.basicConfig(
        level=logging.INFO,
        format='%(asctime)s %(levelname)s %(message)s',
        handlers=[logging.StreamHandler(),
                  #handle log file rollover when the file size exceeds 5 MB
                  RotatingFileHandler('app.log', maxBytes=5 * 1024 * 1024, backupCount=3)
                  #logging.FileHandler('app.log')
                  # handle log file rollover at midnight
                  #TimedRotatingFileHandler('app.log', when='midnight', interval=1, backupCount=7, encoding='utf-8')
                  ])


```

# Async Execution of IO Bound task

```python
async def fetch_data(source, sleep_time=2):
    print("Start fetching data", source)
    await asyncio.sleep(sleep_time)
    print("Data fetched")
    return source


def blocking_fetch_data(source, sleep_time=2):
    print("Start fetching data", source)
    import time
    time.sleep(sleep_time)
    print("Data fetched")
    return source

async def handle_async_io():
task_list = [fetch_data("source1", 2), fetch_data("source2", 1)]
try:
    results = await asyncio.gather(*task_list)
    print(results)
except Exception as e:
    print(f"Exception occurred: {e}")

async def handle_blocking_io():
    loop = asyncio.get_event_loop()
    # Create a ThreadPoolExecutor with a specified number of worker threads
    with ThreadPoolExecutor(max_workers=4) as pool:
        # Submit blocking tasks to be run in different threads using the executor
        tasks = [
            loop.run_in_executor(pool, blocking_fetch_data, source, 2) for source in ["source1", "source2"]
        ]
          try:
            results = await asyncio.gather(*tasks)
            print(f"Results: {results}")
        except Exception as e:
            print(f"Exception occurred: {e}")
        finally:
            print("All tasks completed")


```

# Async Execution of CPU Bound task

For purely CPU-bound workloads, using ProcessPoolExecutor without asyncio is the simpler and more efficient approach.
For applications that require both I/O-bound and CPU-bound tasks to run concurrently, combining asyncio with ProcessPoolExecutor is the best solution. It leverages the strengths of both asynchronous I/O handling and CPU-bound parallelism.

```python
def cpu_bound_task(sleep_time=2):
    import time
    print("Start CPU bound task")
    time.sleep(sleep_time)
    print("CPU bound task completed")
    return sleep_time

async def handle_cpu_bound_task_with_asyncio():
    loop = asyncio.get_event_loop()
    with ProcessPoolExecutor(max_workers=4) as pool:
        tasks = [
            loop.run_in_executor(pool, cpu_bound_task, sleep_timer) for sleep_timer in [2, 1]
        ]
        results = await asyncio.gather(*tasks)
        print(f"CPU Bound Task Result: {results}")


async def handle_cpu_bound_task():
    with ProcessPoolExecutor(max_workers=4) as executor:
        futures = [executor.submit(cpu_bound_task, sleep_timer) for sleep_timer in [2, 1]]

        # Process tasks as they complete
        for future in as_completed(futures):
            print(f"Task result: {future.result()}")

        # for future in futures:
        #     try:
        #         result = future.result()
        #         print(f"CPU Bound Task Result: {result}")
        #     except Exception as e:
        #         print(f"Task generated an exception: {e}")
```
