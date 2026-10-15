# Validator

```ts
@Validator()
export class CreateUserValidator extends AbstractValidator<CreateUserRequest> {
  contructor() {
    super();

    this.ruleFor((x) => x.name)
      .notEmpty()
      .lenght(3, 10);
    
    this.ruleFor((x) => x.email)
      .notEmpty()
      .emailAddress();

    this.ruleFor((x) => x.age).inclusiveBeetwen(18, 60);
  }
}
```
## (Mas ejemplos en Google Drive)