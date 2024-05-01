# Discovering Python Through Microservice Development

As someone deeply rooted in the .Net and Java ecosystems, my programming journey has been full of strongly typed languages and enterprise-level frameworks. However, the allure of Python, with its simplicity and versatility, recently captured my interest. Eager to understand the essence of Python and how it contrasts with the familiar territories of .Net and Java, I embarked on a project that would not only allow me to peek into Python but also to apply it in a real-world scenario. This project took the form of a microservice, aptly named “Equity Store,” designed to fetch stock information by code and exchange.

With “Equity Store,” my objective was to explore Python’s capabilities in microservice architecture, addressing various critical aspects that are pivotal in microservice development, regardless of the programming language used.

## Essential Considerations for Building a Robust Microservice

### API Design

Crafting endpoints that are intuitive and well-structured, ensuring they align with RESTful principles.

### API Versioning

Implementing URL path versioning (e.g., /api/v1/resource) manage changes and maintain backward compatibility with older versions of the API.

```python
eq_api = Api(eq_app, version='1.0', title='Equity Store API', description='Equity Store API', prefix='/api/v1')
```

```python
"""
Register blueprints and api
"""
def register_blueprints_and_api(app, api):
    api.add_namespace(eq_ns)
    api.add_namespace(eq_ex_ns)
    app.register_blueprint(health_bp, url_prefix='/api')
```

### Error Handling

Utilizing Flask’s error handling mechanisms (like @app.errorhandler) to catch exceptions and return informative error responses, improving reliability and user experience.

```python
"""
Global error handlers
"""
def register_error_handlers(app):
    app.register_error_handler(404, error_handlers.not_found)
    app.register_error_handler(500, error_handlers.internal_server_error)

```

### Configuration

Utilized JSON file to configure application settings. This file will be loaded based on the environment variable settings.

```json
FLASK_ENV ="development" or FLASK_ENV ="testing" or FLASK_ENV ="production"
{
  "port": 8080,
  "log_path": "/var/log/stock_info.log",
  "preload_exchanges": "NASDAQ,NYSE",
  "data_source": "database",
  "exchange_query": "SELECT * FROM stocks WHERE exchange = ?",
  "data_sources": {
    "database": {
      "host": "localhost",
      "port": 3306,
      "user": "root",
      "password": "password",
      "database": "stocks"
    }
  }
}

```

### Swagger Documentation

Integrating Swagger UI with Flask using extensions like flasgger to auto-generate interactive API documentation, making it easier for developers to understand and test the API.

```python
@eq_ns.route('')
class Equity(Resource):
    @eq_ns.doc('get_equity')
    @eq_ns.response(201, 'equity details')
    @eq_ns.response(400, 'Internal Error')
    @eq_ns.response(500, 'Internal Server Error')
    @eq_ns.expect(eq_parser)
    def get(self):
        """Get equity"""
        # Implementation omitted for brevity

```

### Logging

Setting up Flask’s built-in logging to capture detailed logs, facilitating easier debugging and monitoring of the microservice.

```python
"""
Initialize logging
"""
"""
Initialize logging
"""
def init_logging(log_path):
        os.makedirs(log_path, exist_ok=True)
        log_file = os.path.join(log_path, 'equity_store.log')
        logging.basicConfig(
            level=logging.INFO,
            format='%(asctime)s - %(levelname)s - %(message)s',
            handlers=[
                logging.FileHandler(log_file),
                #This handler outputs log messages to the console
                logging.StreamHandler()])
```

### Dependency Injection

Applied dependency injection using injector, to decouple components and services, thereby enhancing testability and modularity.

```python
"""
This class is used to bind the services to their implementations and scopes
Steps
1. Add the bindings to factory.development.json
2. Make sure the dependencies are added in the order of their dependencies
3. import the services and their implementations
"""
class DependencyInjectionModules(Module):
    def configure(self, binder):
        try:

            file_path = get_env_factory_file()
            with open(file_path, 'r') as file:
                factory_config = json.load(file)

            for binding in factory_config.get('bindings'):
                binder.bind(
                    eval(binding['service']),
                    to=eval(binding['implementation']),
                    scope=eval(binding['scope']))
            binder.bind(ConfigProvider, to=ConfigProvider, scope=singleton)

        except FileNotFoundError:
            print(f"File not found: {FACTORY_FILE}")
        except Exception as e:
            print(f"Error Configuring Dependency Injection: {e}")
```

A factory file is used to configure dependency injection.

```json
{
  "bindings": [
    {
      "service": "EncryptionService",
      "implementation": "EncryptionService",
      "scope": "singleton"
    },
    {
      "service": "EquityService",
      "implementation": "EquityService",
      "scope": "singleton"
    },
    {
      "service": "DatabaseService",
      "implementation": "DbPostgresService",
      "scope": "request"
    },
    {
      "service": "StockRepository",
      "implementation": "StockRepositoryDisk",
      "scope": "singleton"
    }
  ]
}
```

This is useful when we need variations in deployments.

For example, use the below variations when you want to read the stock information from the database or disk.

```json
{
  "service": "StockRepository",
  "implementation": "StockRepositoryDB",
  "scope": "singleton"
}
```

```json
{
  "service": "StockRepository",
  "implementation": "StockRepositoryDisk",
  "scope": "singleton"
}
```

### Authentication

Securing endpoints using a simple authentication mechanism. Flask extensions like Flask-JWT-Extended can also be used for JWT-based authentication.

```python
@eq_ns.expect(stock_info)
    @requires_auth
    def post(self):
        """Create a new equity """
        return {"message": "Stock info received", "data": eq_ns.payload}, 201


def check_auth(username, password):
    """This function is called to check if a username /
    password combination is valid."""
    return username in users and password == users[username]

def authenticate():
    """Sends a 401 response that enables basic auth"""
    return Response(
    'Could not verify your access level for that URL.\n'
    'You have to login with proper credentials', 401,
    {'WWW-Authenticate': 'Basic realm="Login Required"'})

def requires_auth(f):
    @wraps(f)
    def decorated(*args, **kwargs):
        auth = request.authorization
        if not auth or not check_auth(auth.username, auth.password):
            return authenticate()
        return f(*args, **kwargs)
    return decorated
```

### Encryption of Passwords

Utilizing libraries like Fernet to hash and verify passwords securely, protecting user credentials effectively.

### Health Check

Implementing a health check endpoint (e.g., /health) to provide a simple way to monitor the microservice's status, crucial for maintaining service reliability and performance.

```python
# Create a Blueprint for the health check endpoints
health_bp = Blueprint('health_bp', __name__)

@health_bp.route('/health', methods=['GET'])
def health_check():
    return jsonify({'status': 'UP'}), 200
```

# Implementation omitted for brevity

Tests
Implemented basic tests to demonstrate API endpoint testing.

```python
class ControllerTestCase(unittest.TestCase):
    def setUp(self):
        self.client = eq_app.test_client()
        self.client.testing = True

    @parameterized.expand([
        ("0005.HK", 200),
        ("XXX.TW", 404),
    ])
    def test_get_equity_by_product_code_returns_correct_product_code(self, product_code, expected_status):
        response = self.client.get(f'/api/v1/equity?product_code={product_code}')
        self.assertEqual(response.status_code, expected_status)
        if response.status_code == 200:
            data = response.get_json()
            self.assertEqual(data['product_code'], product_code)

    @parameterized.expand([
        ("HKSE", 200),
        ("XXXX", 404),
    ])
    def test_get_equity_by_exchange_returns_correct_exchange_products(self, exchange_code, expected_status):
        response = self.client.get(f'/api/v1/equity/exchange?exchange_code={exchange_code}')
        self.assertEqual(response.status_code, expected_status)
        if response.status_code == 200:
            data = response.get_json()
            self.assertGreater(len(data), 0)
```

For more information see below:

[Code in github](https://github.com/jpothanc/equity-store/tree/main)

[Readme in github](https://github.com/jpothanc/equity-store/blob/main/README.md)
