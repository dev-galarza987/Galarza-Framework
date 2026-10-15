# Container

## Container
```ts
import { GalarzaFactory } from "@galarza/framework";
import type { IBuilder } from "@galarza/framework";

const builder: IBuilder = GalarzaFactory.create<IRestOptions>();

builder.addControllers();
builder.addMiddlewares();
builder.addInterceptors();
builder.addAuthentications();
builder.addSerializers();
builder.addValidators();
builder.addLoggers();

builder.addSingleton<PostgresService>();
builder.addTransient<IUserRepository, UserRepository>();
builder.addRequest<IUserService, UserService>();

builder.addRegisters(addSecurity());
builder.addRegisters(addPersistence());
builder.addRegisters(add);
```

## Extentions Method
### 1) Functions
```ts
import type { IContainer, IContainerOptions } from "@galarza/framework/di";

export function addSecurity(container: IContainerOptions): IContainer {
  //=> DI Manual
  container
    .addSingleton(TokenService)
    .addSingleton(HahsingService)
    .addSingleton(RateLimiterService);
  
  //=> DI Auto
  container
    .addAuthentication()
    .addAuthorization()
  return container;
}

export function addPersistence(container: IContainerOptions): IContainer {
  container
    .addSingleton<IDatabaseProvider, PostgresProvider>();
    .addSingleton<IUserRepository, UserRepository>();
  return container;
}


builder.container.addSecurity();
builder.container.addPersistence();
```

### 2) Class
```ts
@Module()
export class SecurityModule implements IModuleConfiguration, IDisposable {
  public configure(container: IContainerOptions) {
    container
      .addSingleton(TokenService)
      .addSingleton(HahsingService)
      .addSingleton(RateLimiterService);
    return container;
  }
}
```

### 3) Constant
```ts
export const databaseProvider: IProvider = {
  provide: DRIZZLE_CLIENT,      //--> Simbol()
  inject: [ConfigService],
  useFactory: (configService: ConfigService) => {
    const connectionString = configService.get<string>('DATABASE_URL');
    const host = configService.get<string>('DATABASE_HOST');
  }
}
```


## Application
```ts
import type { IApplication } from "@galarza/framework";

const app: IApplication = builder.build();

app.useRouting();
app.useMiddlewares();
app.useInterceptors();
app.useFilters();
app.useValidators();
app.useSerializers();
app.useOpenApi();
app.useOpenTelemetry();
app.useSecurity();
app.useLogging();
app.userPersistence();

app.listen();
app.close();
app.get<>();
app.resolve<>();
```

### Options DI
```ts
//=> database.options.ts
export class DatabaseOptions implements IDatabaseOptions {}

```

- *.option.ts
- *.config.ts
- *.extention.ts