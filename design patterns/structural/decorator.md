# Decorator

The Decorator Pattern is a structural design pattern that allows behavior to be added to individual objects, dynamically, without affecting the behavior of other objects from the same class. It is often used to adhere to the Single Responsibility Principle, as it allows functionality to be divided between classes with unique areas of concern.

Following example shows, how we can use this pattern to extend the HttpRequest to be cached on a disk or redis.

Component Interface

```csharp
public interface IHttpRequest
{
    Response Request(Request request);
}
```

Concrete Component

```csharp
public class HttpRequest : IHttpRequest
{
    Response Request(Request request)
    {
        //Send HTTP Request and return the Response
    }
}
```

Decorator Base Class

```csharp
public class HttpRequestDecorator : HttpRequest
{
    protected IHttpRequest _httpRequest_;
    HttpRequestDecorator(IHttpRequest httpRequest)
    {
        _httpRequest =  httpRequest
    }

    Response Request(Request request)
    {
        return _httpRequest.Request(request);
    }
}
```

Concrete Decorators

```csharp
public class HttpRequestDiskCache : HttpRequestDecorator
{
    HttpRequestDecorator(IHttpRequest httpRequest) : base(httpRequest) {}

    Response Request(Request request)
    {
        response = _httpRequest.Request(request);
        //if response is not valid, read from the disk and return reponse.
        //cache response on disk;
        return response;
    }
}
```

```csharp
public class HttpRequestRedisCache : HttpRequestDecorator
{
    HttpRequestDecorator(IHttpRequest httpRequest) : base(httpRequest)  { }

    Response Request(Request request)
    {
        response = _httpRequest.Request(request);
        //if response is not valid, read from the redis and return reponse.
        //cache response on redis;
        return response;
    }
}
```

```csharp
    static void Main(string[] args)
    {
        IHttpRequest httpRequest = new HttpRequest();
        httpRequestDiskCache = new HttpRequestDiskCache(httpRequest);
        httpRequestRedisCache = new HttpRequestRedisCache(httpRequest);

        Request request = ();
        request.Url = "https://jsonplaceholder.typicode.com/posts";
        httpRequestDiskCache.Request(request);
        httpRequestRedisCache.Request(request);
    }

```
