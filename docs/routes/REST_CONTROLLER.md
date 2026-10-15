## Controllers (Routes)

```ts
export const ROUTES: IRoute = {
  USER: "/api/v1/users";
}

type HttpMethod = "GET", "POST", "DELETE"


export const UserFindAllOptions: IControllerOptions = {
  method: HttpMethod = "GET",
  statusCode: 200,
  path: "/",
  name: "list-users",
  type: [ListUserResponse],    //=> Dto (Create, Update, etc)
  serializer: [ListUserSerializer],
  validator: [],
  auth: {
    authentication: [],
    authorization: [],
  }
}

@RestController()
@Route(`${ROUTES.USER}`)      //=> @Route("/users")
@UseMiddleware([TokenMiddleware])
@UseInterceptor([AuditInterceptor])
@UseFilter([UserFilterException])
export class UserRestController extends BaseController {
  private readonly service: IUserService;

  constructor(service: IUserService) { this.service = service; }

  @Get(UserFindAllOptions)
  async findAll(): JsonResult<ListUserSerializer> {}
}
```