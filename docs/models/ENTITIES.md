# Entities

```ts
export interface IEntity<TId> {
  public id: TId;   //=> string | number
  public createdAt: Date;
  public updatedAt: Date;
}

export class User implements IEntity<number> {
  //=> IEntity
  public id: number;
  public createdAt: Date;
  public updatedAt: Date;

  public username: string;
  public email: string;
  public password: string;
}
```
