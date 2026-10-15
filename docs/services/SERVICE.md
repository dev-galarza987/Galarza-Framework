# Service @Service()

## Declarative
```ts
@Service()
export class UserService implements IUserService {
  private readonly mapper: IMapper;
  private readonly repository: IRepository;

  constructor(mapper: IMapper, repository: IRepository) {
    this.mapper = mapper;
    this.readonly = repository;
  }
}
```
