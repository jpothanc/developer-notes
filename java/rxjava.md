# RxJava Operators Overview

## Filtering Operators

```java
// Filters items emitted by an Observable.
observable.filter(item -> item % 2 == 0);

// Suppresses duplicate items emitted by an Observable.
observable.distinct();

// Emits only the first N items emitted by an Observable.
observable.take(5);

// Skips the first N items emitted by an Observable.
observable.skip(3);

// Emits an item if a specified timespan has passed without emitting another item.
observable.debounce(500, TimeUnit.MILLISECONDS);

// Transforms each item emitted by an Observable.
observable.map(event -> event.getData());

// Transforms and flattens items emitted by an Observable.
observable.flatMap(event -> fetchDataFromApi(event.getId()));

// Applies an accumulator function to each item sequentially.
observable.scan((accumulator, next) -> accumulator + next);

// Gathers items emitted by an Observable into bundles.
observable.buffer(10);

// Combines emissions from multiple Observables.
Observable.merge(source1, source2);

// Combines emissions from multiple Observables based on a specified function.
Observable.zip(source1, source2, (data1, data2) -> new CombinedData(data1, data2));

// Combines latest emissions from multiple Observables.
Observable.combineLatest(source1, source2, (data1, data2) -> new CombinedData(data1, data2));

// Handles errors by emitting a fallback item.
observable.onErrorReturn(error -> new DefaultData());

// Resubscribes to an Observable sequence in case of errors.
observable.retry(3);

// Continues emitting items after encountering an error.
observable.onErrorResumeNext(source2);

// Specifies the Scheduler on which an Observable should operate.
observable.subscribeOn(Schedulers.io());

// Specifies the Scheduler on which an Observer will observe emissions.
observable.observeOn(AndroidSchedulers.mainThread());

// Executes a side-effect action for each emitted item.
observable.doOnNext(item -> logger.info("Received item: " + item));

// Executes a side-effect action for each error emitted.
observable.doOnError(error -> logger.error("Error occurred: " + error.getMessage()));

// Executes a side-effect action when an Observable completes.
observable.doOnComplete(() -> logger.info("Observation complete"));

```

`subscribeOn`
The subscribeOn operator specifies the Scheduler (thread pool) on which the source Observable will operate. It determines the thread where the subscription to the Observable happens, as well as where the initial emissions occur.

```java
observable.subscribeOn(Schedulers.io())
          .subscribe(item -> logger.info("Received item on IO thread: " + item));
```

`observeOn`
The observeOn operator specifies the Scheduler on which the Observer will observe emissions from the Observable. It controls the thread where downstream operations (like map, filter, etc.) and Observer callbacks (onNext, onError, onComplete) will be executed.

```java
observable.observeOn(Schedulers.newThread())
          .subscribe(item -> updateUI(item));
```

`subscribe`
The subscribe method initiates the subscription to an Observable and defines how to handle emitted items, errors, and completion signals from the Observable.

```java
Disposable disposable = observable.subscribe(
    item -> logger.info("Received item: " + item),
    error -> logger.error("Error occurred: " + error.getMessage()),
    () -> logger.info("Observation complete")
);

// To unsubscribe:
disposable.dispose();

```

`doOnNext`
The doOnNext operator allows you to perform a side-effect action for each emitted item from the Observable, without transforming the item itself. It is often used for logging, updating state, or triggering side effects.

```java
observable.doOnNext(item -> logger.info("Processing item: " + item))
          .map(item -> transformItem(item))
          .subscribe(item -> logger.info("Transformed item: " + item));

```

`onErrorReturn` and `onErrorResumeNext'
The onErrorReturn operator handles errors by emitting a default item and then completing the Observable.

```java
Observable<Integer> observable = Observable.create(emitter -> {
    try {
        emitter.onNext(1);
        emitter.onNext(2);
        // Simulate an error
        int result = 1 / 0; // This will throw an ArithmeticException
        emitter.onNext(3); // This will not be reached
        emitter.onComplete();
    } catch (Exception e) {
        emitter.onError(e);
    }
});

observable
    .onErrorReturn(error -> {
        if (error instanceof ArithmeticException) {
            return -1; // Emitting -1 when ArithmeticException occurs
        } else {
            throw new RuntimeException("Unknown error occurred");
        }
    })
    .subscribe(
        item -> System.out.println("Received item: " + item),
        error -> System.err.println("Error occurred: " + error.getMessage()),
        () -> System.out.println("Observation complete")
    );


    Observable<Integer> fallback = Observable.range(10, 3); // Fallback Observable emitting 10, 11, 12

    observable
        .onErrorResumeNext(fallback)
        .subscribe(
            item -> System.out.println("Received item: " + item),
            error -> System.err.println("Error occurred: " + error.getMessage()),
            () -> System.out.println("Observation complete")
        );


```

# Commonly Used Schedulers in RxJava

- **Schedulers.computation()**: For computational or CPU-bound tasks. Limited by the number of available CPU cores.

- **Schedulers.io()**: For I/O-bound tasks, such as network or file operations. Manages a pool of threads.

- **Schedulers.newThread()**: Creates a new thread for each unit of work. Not recommended for long-running operations due to the overhead of thread creation.

- **Schedulers.single()**: Executes tasks in a single thread sequentially. Useful for tasks that require strict execution order.

- **AndroidSchedulers.mainThread()**: Android-specific scheduler that schedules actions to be executed on the main UI thread.

- **Schedulers.trampoline()**: Executes tasks one after another on the current thread, often used for recursive tasks or executing actions sequentially.

- **Schedulers.from(Executor)**: Converts a standard `java.util.concurrent.Executor` into a Scheduler.

## What is Backpressure and How to Handle It

Backpressure refers to the situation where the rate of data production exceeds the rate of data consumption downstream. This can lead to issues such as memory leaks, system instability, or data loss if not handled properly.

```java
   //First you need to convert your observable to flowable
    Flowable<String> flowable = eventPublisher.subscribe().
                             toFlowable(BackpressureStrategy.BUFFER);

    Disposable disposable = flowable
            .subscribeOn(Schedulers.io())
            //All items will be received here
            .doOnNext(item -> System.out.println("Received item: " + item))
            .observeOn(Schedulers.computation())
            //only one item per 5 seconds will be emited below.
            .onBackpressureBuffer()
            .subscribe(item -> {
                System.out.println("\nData received: " + item + " Thread:"+ Thread.currentThread().getName());
                TimeUnit.SECONDS.sleep(5);
            });
```

# An Example how to use this in a function

```java
 public  Observable<Order> dispatchOrder(String orderId) {

    OrderService orderService = new OrderService();
    return Observable.defer(() -> {
                System.out.println("Fetching order: " + orderId + " on thread: " + Thread.currentThread().getName());
                Order order = orderService.getOrder(orderId);
                return Observable.just(order);
            })
            .subscribeOn(Schedulers.io()) // Fetch order on IO scheduler
            .observeOn(Schedulers.computation())
            .map(orderService::enrichOrder)
            .map(orderService::performPayment)
            .map(orderService::dispatchOrder)
            .doOnNext(order -> {
                System.out.println("Sending email for order: " + order.getId() + " on thread: " + Thread.currentThread().getName());
                orderService.sendEmail(order);
            })
            .doOnError(error -> {
                System.out.println("Error occurred on thread: " + Thread.currentThread().getName() + ": " + error.getMessage());
            })
            .doOnComplete(() -> System.out.println("Completed emission"))
            .doFinally(() -> System.out.println("Observable completed"));
}
```
