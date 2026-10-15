# Options de DI

## Provider
## ClassProvider
```ts
export const classProvider: ClassProvider<TProvider> = {
  provider: InjectionToken,
  userClass: Type<TProvider>,
  scope: Scope.SINGLETON,
  inject: [ConfigService],
  durable: boolean = true,
}
```

## ValueProvider
```ts
export const classProvider: ClassProvider<TProvider> = {
  provider: InjectionToken,
  useValue: TProvider,
  inject: never,
}
```

## FactoryProvider
```ts
export const classProvider: ClassProvider<TProvider> = {
  provider: InjectionToken,
  useFactory: async (...args: any[]): Promise<TProvider> {}
  inject: Array<InjectionToken | OptionalFactoryDependencie> = [],
  scope: Scope.TRANSIENT,
  durable: false,
}
```

## ExistingProvider
```ts
export const classProvider: ClassProvider = {
  provider: InjectionToken,
  useExisting: any;
}
```