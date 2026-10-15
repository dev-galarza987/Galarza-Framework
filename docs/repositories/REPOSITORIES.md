# Repository

```ts
@Repository()
export class UserPostgresRepository extends BaseRepository<User> {
  //--> Use (TypeORM, Mikro ORM, Drizzle ORM, Prisma)
  async findByEmail(email: string): Promise<Result<User, Exception>> {}
  async findByEnable(enable: boolean): Promise<Result<User, Exception>> {}
}
```