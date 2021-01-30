
### Setup a SSR project with Angular Universal

The official documentation doesn't cover a lot about [angular universal](https://angular.io/guide/universal)

_To generate a project_

```bash
ng new myNewProjectName && cd ./myNewProjectName

ng add @nguniversal/express-engine --clientProject myNewProjectName

npm run build:ssr && npm run serve:ssr
```

To start the client version for development
`ng serve`

_Error: More than one module matches. Use skip-import option to skip importing the component into the closest module_

Adding a component with the standard Angular method: `ng -g componentName` will return the following error _More than one module matches. Use skip-import option to skip importing the component into the closest module_ because the application contains a server and a client module.

To add the component:

`ng g c componentName --module app`
