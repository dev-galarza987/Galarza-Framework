# Plugins

```ts
export interface IPlugin {
  public id: string;
  public name: string;
  public description: string;
  public components: IComponent[];

  async install(app: IApplication): Promise<void>;
  async uninstall(): Promse<void>; 
}

export class EmailPlugin implements IPlugin {
  //
}
```

## Components
- Services
- Options
- Repositories
