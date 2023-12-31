# Personal Documentation for relevant topics and keywords

This personal documentation can be best used by using CTRL + F to search for specific keywords.

## Common Terms

- _extends_: It's used for class inheritance. When you use extends, the class you are defining inherits properties and methods from the base class. Inheritance is a way to create a new class from an existing class. The new class (child class) gets access to the properties and methods of the existing class (parent class), allowing for code reuse and maintaining a hierarchical class structure.

- _implements_: It's used when a class intends to fulfill the contract provided by an interface. An interface in TypeScript is a structure that defines a contract in your application. It defines the syntax for classes to follow. Classes that implement an interface must provide an implementation for all the properties and methods defined in the interface.

## Helpful Links

- [What is idempotency in HTTP methods?](https://stackoverflow.com/questions/45016234/what-is-idempotency-in-http-methods)
- [How To Format Code with Prettier Extension in Visual Studio Code](https://www.digitalocean.com/community/tutorials/how-to-format-code-with-prettier-in-visual-studio-code)
- [Running Promises In Parallel: A Visual Guide (Promise.all(), Promise.allSettled(), Promise.race(), Promise.any())](https://julesblom.com/writing/running-promises-in-parallel)
- [Understanding JWTs](https://dev.to/philip-ainberger/understanding-jwts-a-simple-guide-for-beginners-aba)
- [API Integration Patterns – The Difference between REST, RPC, GraphQL, Polling, WebSockets and WebHooks](https://www.freecodecamp.org/news/api-integration-patterns/)
- [Common mistakes with the Next.js App Router and how to fix them](https://vercel.com/blog/common-mistakes-with-the-next-js-app-router-and-how-to-fix-them)

## Nest.js

This section includes relevant information for Nest.js (Node.js framework).

### Commands

- Install Nest.js CLI: `npm i -g @nestjs/cli`
- Install Nest.js application in the current directory (without creating a new folder): `nest new .`
- Create module / controller / provider / : `nest g module name` / `nest g controller name` / `nest g provider name`
- Start the server: `npm run start:dev`
- Used for PartialType for DTOs (see corresponding section): `npm i @nestjs/mapped-types -D`
- Used for decorator-based validation: `npm i --save class-validator class-transformer`

### `ConfigModule.forRoot()` to make environment variables work

1. Install the Nest.js config module `npm i --save @nestjs/config`. It relies on dotenv.
2. Create an `.env` file in the root folder and add the key/value pairs e.g. `DATABASE_USER=myusername`.
3. Open `app.module.ts` and import the config module: `import { ConfigModule } from '@nestjs/config';`
4. Add `ConfigModule.forRoot()` to the imports section of `app.module.ts`. It will load the contents of the `.env` file automatically.
5. Then you can begin to use the environment variables with `process.env.<variable_name>` in the database config section e.g.

### EntityRepositories & EntitiyManager & orm

Entity Repositories are thin layers on top of EntityManager. They act as an extension point, so we can add custom methods, or even alter the existing ones. The default, EntityRepository implementation just forwards the calls to underlying EntityManager instance - [click for more information](https://mikro-orm.io/docs/repositories)

To make use of the EntityRepositories in the modules, you would have to implement `MikroOrmModule.forFeature([entity_name])`. To make use of the `orm` class you would have implement `MikroOrmModule` as a provider (I think).

### Error Handling

Make use of HttpException instead of `throw new Error()` in order to create relevant errors with easier access to a corresponding body with message and status.

```js
getSingleUserWithID(id: string): IUSERDATA {
    const IDNumber: number = parseInt(id);

    if (isNaN(IDNumber)) {
      throw new HttpException(
        'Invalid ID format, number format required.',
        HttpStatus.BAD_REQUEST,
      );
    }

    const user = USERDATA.find((ele: IUSERDATA) => ele.id === IDNumber);

    if (user) {
      return user;
    } else {
      throw new HttpException(
        'User not found for this ID.',
        HttpStatus.NOT_FOUND,
      );
    }
  }
```

### Pipes

[Pipes on Nest.js docs](https://docs.nestjs.com/pipes)
Middleware for transformation and validation of the request data

```js
@Get(':id')
  getSingleUserWithID(
    @Param('id', ParseIntPipe) id: number,
  ): IUSERDATA | undefined {
    return this.usersService.getSingleUserWithID(id);
  }
```

### DTO (Data Transfer Object) Schemas

[DTO Schemas on Nest.js docs](https://docs.nestjs.com/controllers#request-payloads)
A DTO is an object that defines how the data will be sent over the network. Use classes instead of TypeScript interfaces.

```js
// in /users/dto/create-user.dto.ts
export class CreateUserDto {
  name: string;
  email: string;
  role: "INTERN" | "ENGINEER" | "ADMIN";
}
```

```js
// in /users/dto/update-user.dto.ts
import { CreateUserDto } from "./create-user.dto";
import { PartialType } from "@nestjs/mapped-types";

// Makes CreateUserDto fields optional (not everything has to be updated with each request)
export class UpdateUserDto extends PartialType(CreateUserDto) {}
```

### Decorator-based validation

[Validation decorators](https://github.com/typestack/class-validator#validation-decorators)

```js
import { IsEmail, IsEnum, IsNotEmpty, IsString } from "class-validator";

export class CreateUserDto {
  @IsString()
  @IsNotEmpty()
  name: string;

  @IsEmail()
  email: string;

  @IsEnum(["INTERN", "ENGINEER", "ADMIN"], {
    message: "Valid role required.",
  })
  role: "INTERN" | "ENGINEER" | "ADMIN";
}
```

```js
// ValidationPipe has to be included, otherwise the validation won't work.
@Post() // POST /users
  create(@Body(ValidationPipe) createUserDto: CreateUserDto) {
    return createUserDto;
  }
```

### @Query & @Param

[Click for more information](https://stackoverflow.com/questions/54958244/how-to-use-query-parameters-in-nest-js)

If you have you a parameter as part of an url `/articles/${articleId}/details`, you would use @Param:

```js
@Get('/articles/:ARTICLE_ID/details')
async getDetails(
    @Param('ARTICLE_ID') articleId: string
): Promise<any> {
  ...
  }
```

If you want to provide query parameters `/article/findByFilter/bug?google=1&baidu=2`, you would use @Query:

```js
@Get('/article/findByFilter/bug?')
async find(
    @Query('google') google: number,
    @Query('baidu') baidu: number,
): Promise<any> {
  ...
  }
```

### Rate Limits

Too limit the amount of incoming requests you can use `npm i @nestjs/throttler` and make the corresponding changes in the module file (See [Nest.js REST API with CORS, Rate Limits, Server Logs, & Exception Filter](https://www.youtube.com/watch?v=hQTtioSw4Zo&list=PL0Zuz27SZ-6MexSAh5x1R3rU6Mg2zYBVr&index=7) for some examples). You could also add specific throttle logic for single routes in the controller (Takes precedence over the throttle logic in the module file) with `@Throttle({ short: {ttl: 1000, limit: 1 }})`, for example.

```js
// This is in app.module.ts
import { Module } from "@nestjs/common";
import { AppController } from "./app.controller";
import { AppService } from "./app.service";
import { UsersModule } from "./users/users.module";
import { ThrottlerModule, ThrottlerGuard } from "@nestjs/throttler";
import { APP_GUARD } from "@nestjs/core";

@Module({
  imports: [
    UsersModule,
    ThrottlerModule.forRoot([
      {
        name: "short",
        ttl: 5000,
        limit: 3,
      },
      {
        name: "long",
        ttl: 60000,
        limit: 100,
      },
    ]),
  ],
  controllers: [AppController],
  providers: [AppService, { provide: APP_GUARD, useClass: ThrottlerGuard }],
})
export class AppModule {}
```

### Testing in Nest.js

This is a test file for the corresponding controller. Remember to include all relevant controllers and services. A potential source of error could be incorrect or missing asynchronous logic in the controller.

```js
import { Test, TestingModule } from '@nestjs/testing';
import { UsersController } from './users.controller';
import { IUSERDATA, UsersService } from './users.service';

describe('UsersController', () => {
  let controller: UsersController;
  let service: UsersService;

  beforeEach(async () => {
    const module: TestingModule = await Test.createTestingModule({
      controllers: [UsersController],
      providers: [UsersService],
    }).compile();

    controller = module.get<UsersController>(UsersController);
    service = module.get<UsersService>(UsersService);
  });

  describe('/users', () => {
    it('should return users with a specific role', async () => {
      const role = 'ADMIN'; // Change this to the role you want to test

      const mockUsers: IUSERDATA[] = [
        {
          id: 1,
          name: 'Bub Bilbo',
          email: 'Bub.Bilbo@Bilbo.com',
          role: 'INTERN',
        },
        {
          id: 2,
          name: 'Kamin Ka',
          email: 'disposableEmail@temporary.com',
          role: 'INTERN',
        },
        { id: 3, name: 'Hajin', email: 'Hajin.Ma@gmx.de', role: 'ADMIN' },
      ] as IUSERDATA[];

      jest.spyOn(service, 'getUsers').mockResolvedValue(mockUsers);

      const result = await controller.getUsers(role);

      expect(result).toEqual(mockUsers);
    });
  });

  describe('update', () => {
    it('should correctly update a user with the given id and return updated user data', () => {
      const id = '1';
      const updateUserDto = {
        name: 'Updated Name',
        email: 'updated.email@example.com',
      };

      const result = controller.update(id, updateUserDto);

      expect(result).toEqual({ id, ...updateUserDto });
    });
  });

  describe('getSingleUserWithID', () => {
    it('should return a user with the specified ID', async () => {
      const user: IUSERDATA = {
        id: 1,
        name: 'Bub Bilbo',
        email: 'Bub.Bilbo@Bilbo.com',
        role: 'INTERN',
      };

      jest.spyOn(service, 'getSingleUserWithID').mockImplementation(() => user);

      const result = controller.getSingleUserWithID(1);

      expect(result).toEqual(user);
    });

    it('should handle the case where a user with the given ID does not exist', async () => {
      const userId = 999; // Non-existent user ID

      jest
        .spyOn(service, 'getSingleUserWithID')
        .mockImplementation(() => undefined);

      const result = controller.getSingleUserWithID(userId);

      expect(result).toBeUndefined();
    });
  });
});
```

### MikroORM in Nest.js

Install relevant dependencies: `npm i -s @mikro-orm/core @mikro-orm/nestjs @mikro-orm/mariadb` (for mariadb) - [click for more information](https://mikro-orm.io/docs/usage-with-nestjs)

MikroORM requires a configuration file. This file specifies how MikroORM connects to your MariaDB database and manages entities. Create a file named `mikro-orm.config.ts` in your project's root directory with the following content:

```js
import { MariaDbDriver, Options } from '@mikro-orm/mariadb';

@Module({
  imports: [MikroOrmModule.forRoot({
  dbName: 'your_database_name',
  type: 'mariadb',
  host: 'localhost',
  port: 3306,
  user: 'your_username',
  password: 'your_password',
  entities: ['dist/**/*.entity.js'],  // Production
  entitiesTs: ['src/**/*.entity.ts'], // Development (TypeScript)
  driver: MariaDbDriver,
  }),
  // ... other imports,
  ]
  providers: [PhotoService],
  controllers: [PhotoController],
})
```

To integrate MikroORM with Nest.js, you have to set up a module. You can either use the MikroOrmModule.forRoot() method for root configuration or MikroOrmModule.forRootAsync() for asynchronous configuration.

In your main application module (usually app.module.ts), add the following:

```js
import { Module } from "@nestjs/common";
import { MikroOrmModule } from "@mikro-orm/nestjs";
import mikroOrmConfig from "./mikro-orm.config";

@Module({
  imports: [MikroOrmModule.forRoot(mikroOrmConfig)],
  // ... other configurations
})
export class AppModule {}
```

#### Entities

Entities in MikroORM are like models representing your database tables. Create a directory for your entities (e.g., entities) and define your entities there. Here's a simple example:

```js
import { Entity, PrimaryKey, Property } from '@mikro-orm/core';

@Entity()
export class User {
  @PrimaryKey()
  id!: number;

  @Property()
  name!: string;

  // ... other properties
}
```

Now, you can inject the EntityManager from MikroORM into your services or controllers to interact with the database.

```js
import { Injectable } from '@nestjs/common';
import { EntityManager } from '@mikro-orm/mariadb';
import { User } from './entities/user.entity';

@Injectable()
export class UserService {
  constructor(private readonly entityManager: EntityManager) {}

  async findAll(): Promise<User[]> {
    return await this.entityManager.find(User, {});
  }

  // ... other methods
}
```

#### The `dist` Folder

The dist folder, short for "distribution", is a common naming convention used in many software projects, especially those involving JavaScript and TypeScript. It serves as the output directory where the compiled, built, or transpiled code is placed. This folder is what you typically deploy to your production environment, as it contains the optimized and runnable version of your application code.

#### Glob Pattern

**/\*.entity.js: This is a glob pattern. The ** part means "any directory", and \*.entity.js means "any file that ends with .entity.js". So, this pattern will match all JavaScript files ending with .entity.js in any subdirectory of dist.

#### HeidiSQL vs. MikroORM

HeidiSQL is a popular database management tool that provides a graphical user interface (GUI) to interact with various types of SQL databases, including MariaDB. Here are some common uses for HeidiSQL in your development workflow:

- Database Administration: HeidiSQL allows you to perform administrative tasks like creating databases, modifying tables, managing indexes, and setting up foreign key relationships.
- Data Visualization and Editing: It provides an easy-to-use interface for viewing, adding, editing, and deleting data in your database tables.
- Query Execution: You can write and execute SQL queries directly, which is helpful for testing queries, exploring data, or performing complex database operations that might not be straightforward through an ORM.
- Database Debugging and Optimization: HeidiSQL can be used to analyze and optimize SQL queries, view query execution plans, and diagnose performance issues.
- Exporting and Importing Data: It offers tools for exporting data (e.g., to SQL dumps, CSV files) and importing data from various sources.

MikroORM, on the other hand, is an Object-Relational Mapping (ORM) tool used within your Nest.js application. Its roles include:

- Entity Management: MikroORM lets you define entities in your codebase, which map to tables in your MariaDB database.
- Database Interactions in Code: It abstracts the database interactions, allowing you to write database queries using JavaScript or TypeScript, without writing raw SQL.
- Data Manipulation and Retrieval: You can use MikroORM to create, read, update, and delete records in your database through your application's code.
- Migrations: MikroORM can handle database migrations, which are useful for managing changes to your database schema over time.

In a typical development workflow:

- Use HeidiSQL for direct database interactions, schema creation, data visualization, and manual querying. It's particularly useful during the initial stages of database design or when you need to perform complex operations that are easier to handle with a GUI.
- Use MikroORM within your Nest.js application for all database interactions that your application needs to perform programmatically. This includes CRUD operations, business logic implementation, and handling relational data through entities.

#### Inserting Data into the Database

1. Creating an Entity: In MikroORM, you first create an entity instance with the data you want to insert into your database. This is usually done using the create method on your entity repository or by simply creating a new instance of the entity class and setting its properties.

2. Persisting the Entity: The persist function is used to make MikroORM aware of the entity instance you wish to save to the database. It doesn't immediately execute a database insert operation. Instead, it tells MikroORM to "track" this entity as something that will need to be saved to the database. You can think of this as a way to prepare or stage your data for insertion.

3. Flushing the Changes: The flush function is what actually triggers the communication with the database. When you call flush, MikroORM looks at all the entities it has been told to track (through persist) and performs the necessary insert, update, or delete operations on the database. This is the point where your data is actually saved to the database.

The reason for this two-step process (persist, then flush) is to allow for more efficient database operations. By collecting several changes and then applying them all at once in a single flush, MikroORM can optimize database access, reduce the number of individual transactions, and maintain transactional integrity.

#### Naming Convention for Entities

In MikroORM when using it with Nest.js (or in any other context), the entity name and the database table name don't necessarily have to match exactly, but there needs to be a clear association between them. The convention in many ORM frameworks, including MikroORM, is to name entities in singular form (e.g., Coupon) and tables in plural form (e.g., coupons). However, this convention is not a strict requirement, and you can configure MikroORM to map entity names to specific table names as needed.

In MikroORM, as with many ORM (Object-Relational Mapping) frameworks, there's a common convention to use snake_case for database column names, especially when working with certain databases like PostgreSQL or MySQL. This convention is not a strict rule, but it is widely adopted due to its readability and compatibility with SQL standards.

Here's how the process typically works:

1. Entity Class Definition: You define an entity class (e.g., Coupon) in your application code. This class represents a table in your database (e.g., coupons).

2. Table Mapping: By default, MikroORM will try to map your entity class to a table in the database by converting the class name from singular to plural and by following specific naming conventions (like camelCase to snake_case). However, if your table name doesn't follow these conventions, you need to explicitly specify the table name.

3. Explicit Table Naming: You can use the @Entity decorator to explicitly define the table name associated with an entity. For example, if your entity is named Coupon but your table is named coupons, you can specify this like so:

```js
@Entity({ tableName: "coupons" })
export class Coupon {
  // ... entity properties ...
}
```

This tells MikroORM exactly which table this entity corresponds to, regardless of the naming convention.

4. Repository and Database Interaction: When you interact with the database through a repository, MikroORM uses the mapping information from your entity class to know which table to query or modify. The entity class acts as a blueprint for how the data should be structured and how it relates to the database schema.

If you want to use the singular form Coupon and still map it to the coupons table, you should explicitly set the tableName in the @Entity decorator as shown above.

Automatic vs. Manual Mapping: By default, MikroORM will try to automatically convert camelCase property names in your entities to snake_case column names in the database. However, if your database schema doesn't follow this convention, or if you prefer a different naming style, you might encounter issues. In such cases, you have to explicitly specify the column names using decorators, like so:

```js
@Entity()
export class User {
  @Property({ columnType: "int", fieldName: "user_id" })
  userId: number;

  @Property({ columnType: "varchar", fieldName: "user_name" })
  userName: string;
  // ...
}
```

In the above example, userId and userName are camelCase properties in your entity, but they are explicitly mapped to user_id and user_name in the database.

#### DTO & Entity Usage in a POST Request (Example)

_1. User Entity (User.ts):_
This is a basic user entity that corresponds to your users table in the database.

```js
import { Entity, PrimaryKey, Property } from "@mikro-orm/core";

@Entity()
export class User {
  @PrimaryKey()
  @SerializedPrimaryKey()  // This decorator is useful when using non-numeric primary keys like UUIDs
  id!: number;  // '!' is used to tell TypeScript that this field will be populated automatically

  @Property()
  username: string;

  @Property()
  email: string;

  // ... other properties like password, etc.
}
```

_2. DTO for Creating User (create-user.dto.ts):_
This DTO will be used to receive data from the POST request.

```js
export class CreateUserDto {
    readonly username: string;
    readonly email: string;
    // ... other relevant properties
}
```

_3. User Service (user.service.ts):_
This service handles the business logic, including interacting with the database using MikroORM.

```js
import { Injectable } from '@nestjs/common';
import { User } from './entities/user.entity';
import { CreateUserDto } from './dto/create-user.dto';
import { EntityRepository } from '@mikro-orm/core';

@Injectable()
export class UserService {
    constructor(
        @InjectRepository(User)
        private readonly userRepository: EntityRepository<User>,
    ) {}

    async createUser(createUserDto: CreateUserDto): Promise<User> {
        const user = this.userRepository.create(createUserDto);
        await this.userRepository.persistAndFlush(user);
        return user;
    }
}
```

_4. User Controller (user.controller.ts):_
The controller handles the HTTP requests. The POST route uses the CreateUserDto.

```js
import { Controller, Post, Body } from '@nestjs/common';
import { CreateUserDto } from './dto/create-user.dto';
import { User } from './entities/user.entity';
import { UserService } from './user.service';

@Controller('users')
export class UserController {
    constructor(private readonly userService: UserService) {}

    @Post()
    async createUser(@Body() createUserDto: CreateUserDto): Promise<User> {
        return this.userService.createUser(createUserDto);
    }
}
```

_Summary_

- The CreateUserDto is used in the controller to define the shape of the data received from the client.
- The service receives the CreateUserDto, uses it to create a new User entity instance, and then persists this instance to the database.
- The entity User represents the structure of your database table and is used for database operations.
- This separation ensures that the input data is validated and transformed as needed before being used to create a new entity in the database.

#### Steps to Use UUIDs in MikroORM

If you're using a database that doesn't natively generate UUIDs, you might need to use an external package like uuid to generate them. Install it via npm if needed (`npm install uuid`).

Example:

```js
import { Entity, PrimaryKey, Property } from "@mikro-orm/core";
import { v4 as uuidv4 } from "uuid";

@Entity()
export class User {
  @PrimaryKey({ type: "uuid" })
  id: string = uuidv4();

  @Property()
  username: string;

  @Property()
  email: string;

  // ... other properties ...
}
```

When you create a new user in your service, MikroORM will handle the UUID generation (no extra steps required at this point).

## Tailwind CSS

This section includes relevant information for Tailwind CSS (CSS framework).

### Skeleton Loader (Pulse Effect)

Uses `animate-pulse` to create the typical skeleton pulse effect ([source](https://tailwindcss.com/docs/animation)).

```js
<div class="border border-blue-300 shadow rounded-md p-4 max-w-sm w-full mx-auto">
  <div class="animate-pulse flex space-x-4">
    <div class="rounded-full bg-slate-700 h-10 w-10"></div>
    <div class="flex-1 space-y-6 py-1">
      <div class="h-2 bg-slate-700 rounded"></div>
      <div class="space-y-3">
        <div class="grid grid-cols-3 gap-4">
          <div class="h-2 bg-slate-700 rounded col-span-2"></div>
          <div class="h-2 bg-slate-700 rounded col-span-1"></div>
        </div>
        <div class="h-2 bg-slate-700 rounded"></div>
      </div>
    </div>
  </div>
</div>
```
