# Personal Documentation for relevant topics and keywords

This personal documentation can be best used by using CTRL + F to search for specific keywords.

## Nest.js

This section includes relevant information for Nest.js (Node.js framework).

### Commands

- Install Nest.js CLI: `npm i -g @nestjs/cli`
- Create module / controller / provider / : `nest g module name` / `nest g controller name` / `nest g provider name`
- Start the server: `npm run start:dev`

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
