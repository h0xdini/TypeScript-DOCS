# TypeScript-DOCS

## Why TypeScript?
![1](https://user-images.githubusercontent.com/77200870/188300785-de1534d0-2dc0-49bd-9a46-fe82d71df3bf.PNG)

<br/>

## Course Overview
![2](https://user-images.githubusercontent.com/77200870/188300772-45d15b0d-a7ea-4a8d-9c01-e09f52e07cc4.PNG)

<br/>

## 0x0 - Basic Types
### The problem 🚧
```js
const message = "Hello World!";

message();
```
> This won't produce any error during development, only when we run the above code we will get a `TypeError` because the JavaScript runtime figures the type of the value and lists the behaviors and capabilities it has.

### The solution ✔️
> TypeScript solves this thanks to its `static type-checker`

<br/>

### The problem 🚧 : Non-exception Failures
> So far we’ve been discussing certain things like runtime errors - cases where the JavaScript runtime tells us that it thinks something is nonsensical. Those cases come up because the ECMAScript specification has explicit instructions on how the language should behave when it runs into something unexpected.
For example, the specification says that trying to call something that isn’t callable should throw an error. Maybe that sounds like “obvious behavior”, but you could imagine that accessing a property that doesn’t exist on an object should throw an error too. Instead, JavaScript gives us different behavior and returns the value undefined

```js
const user = {
  name: "Daniel",
  age: 26,
};
user.location; // returns undefined
```

### The solution ✔️
> Using the TS static type-checker
![ts1](https://user-images.githubusercontent.com/77200870/188301352-0307ae22-285c-478b-9ef4-0978d9d331e8.PNG)

<br/>

### The problem 🚧 : Legitimate Bugs
#### [1] Typos
![ts2](https://user-images.githubusercontent.com/77200870/188301427-db416fae-bf55-4393-bf98-2d660d7799c4.PNG)
#### [2] uncalled functions
![ts3](https://user-images.githubusercontent.com/77200870/188301465-58e28f16-7f72-4134-8b73-3d4d93e67372.PNG)
#### [3] Basic Logic Errors
![ts5](https://user-images.githubusercontent.com/77200870/188301488-b41113fb-25a4-473c-af0d-50789de889f4.PNG)

