# NestJS

## Why NestJS?

[Nest](https://docs.nestjs.com/) provides an out-of-the-box application architecture which allows developers and teams to create highly testable, scalable, loosely coupled, and easily maintainable applications. The architecture is heavily inspired by Angular.

------

### **INSTALLATION**

```bash
npm i -g @nestjs/cli
```

### **CREATE NEW PROJECT**

```bash
nest new project-name
```

------

**main.ts** is the entry point of the app that calls function **bootstrap**

```ts
import { NestFactory } from '@nestjs/core';
import { AppModule } from './app.module';

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  await app.listen(3000);
}
bootstrap();
```

### What are Modules ?

`Modules` are the actual features which includes `controllers, services/providers`. Modules should be specific to features.

```ts
import { Module } from '@nestjs/common';
import { AppController } from './app.controller';
import { AppService } from './app.service';

@Module({
  imports: [],
  controllers: [AppController],
  providers: [AppService],
})
export class AppModule {}
```

Modules can be dependent on other modules also.

### What are Controllers ?

`Controllers` holds the actual business logic to be executed. They parse the request and sends back the response. The usually interact with `Providers`. Also `controllers` will not have direct access to database.

```ts
import { Controller, Get } from '@nestjs/common';
import { AppService } from './app.service';

@Controller()
export class AppController {
  constructor(private readonly appService: AppService) {}

  @Get()
  getHello(): string {
    return this.appService.getHello();
  }
}
```

### What are Providers ?

`Providers` always acts as bridge between controller and backend. They actually interact with the database and serve controllers.

```ts
import { Injectable } from '@nestjs/common';

@Injectable()
export class AppService {
  getHello(): string {
    return 'Hello World!';
  }
}
```

Services and Controllers are scopped to Modules.

### What are decorators?

`@Module, @Get` are kind of decorators. They have special meaning. Decorators defines the job. They will take a set of instructions/configuration to do the job.

`@Controller()` will be used to route the incoming request. `@Controller()` will accept all requests. `@Controller('/users')` will accept the requests with **/users**.

`@Get()` will take all incoming `/` request. `@Get('/products')` will take request with only `/products`.

**NestJs** by default sets the content type and headers. If the return value is string, it is set to `html/text`. If the return value is object, it is set to `application/json` by default.

We can also set custom headers using `@Header()` decorator

```ts
@Get()
@Header('Content-type', 'text/html')
  getHello(): string {
    return this.appService.getHello();
  }
```

#### Getting values in params

```ts
@Get('/:id')
getProduct(@Param('id') productId: string): Product {
  return this.productsService.getProduct(productId);
}
```

#### Getting values in body

```ts
@Post()
addProduct(
  @Body('title') prodTitle: string,
  @Body('description') prodDescription: string,
  @Body('price') prodPrice: number,
): { id: string } {
  const id = this.productsService.insertProduct(
    prodTitle,
    prodDescription,
    prodPrice,
  );
  return { id: id };
}
```
