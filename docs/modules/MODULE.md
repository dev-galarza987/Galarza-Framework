# Module

```ts
@Module({
  modules: [PostModule],
  controllers: [UserRestController, UserWebController],
  services: [UserService],
  repositories: [UserRepository],
  plugins: [],
  components: {
    validators: [],
    serializers: [],
    middlewares: [],
    interceptors: [],
    mappers: [],
    entities: [],
    filters: [],
    loggers: [],
    exceptions: []
  }
  exports: [UserService]
})
export class UserModule {}
```