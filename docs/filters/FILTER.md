# Filters Exception

```ts
@Catch()
export class GlobalExceptionFilter implements IExceptionFilter {
  catch(exception: Exception, context: ExecutionContext) {
    const httpContext = context.switchToHttp();
    const response = http.getResponse<IResponse>();
    const request = httpContext.getRequest<IRequest>();
    const status = exception.getStatus();

    respose
      .status(status)
      .json({
        statusCode: status,
        timestamp: new Date().toISOString(),
        path: request.url,
      });
  }
}
```