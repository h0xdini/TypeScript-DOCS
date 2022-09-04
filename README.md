# TypeScript-DOCS

## Why TypeScript?
![1](https://user-images.githubusercontent.com/77200870/188300785-de1534d0-2dc0-49bd-9a46-fe82d71df3bf.PNG)

<br/>

## Course Overview
![2](https://user-images.githubusercontent.com/77200870/188300772-45d15b0d-a7ea-4a8d-9c01-e09f52e07cc4.PNG)

<br/>

## 0x0 - TypeScript Types
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

--------------------------------------------------------------
### Types for Tooling 🔨
> TypeScript core type-checker can provide error messages and code completion as you type in the editor, that's what people refer to as `tooling in TypeScript`
But tooling in TypeScript goes beyond completions and errors as you type. An editor that supports TypeScript can deliver “quick fixes” to automatically fix errors, refactorings to easily re-organize code, and useful navigation features for jumping to definitions of a variable, or finding all references to a given variable. All of this is built on top of the type-checker and is fully cross-platform.

![ts6](https://user-images.githubusercontent.com/77200870/188301702-fc8f33b6-7730-48ff-86f7-07a46cb74cac.PNG)

<br/>

### Explicit Types
> With TypeScript we can add `type annotations` on variables and function paramaters
```ts
function greet(person: string, date: Date) {
  console.log(`Hello ${person}, today is ${date.toDateString()}!`);
}
```
<p>Date() in JavaScript returns a string</p>

![ts7](https://user-images.githubusercontent.com/77200870/188301828-5d469bf9-3976-4aaa-8788-be70afac998d.PNG)

> Keep in mind, we don’t always have to write explicit type annotations. In many cases, TypeScript can even just infer (or “figure out”) the types for us even if we omit them (Type Inference).

![ts8](https://user-images.githubusercontent.com/77200870/188301879-92b91205-e624-4c4e-bceb-25a1b5f771fe.PNG)

>Even though we didn’t tell TypeScript that `msg` had the type `string` it was able to figure that out. That’s a feature, and it’s best not to add annotations when the type system would end up inferring the same type anyway.

#### All TypeScript Basic Types
![4](https://user-images.githubusercontent.com/77200870/188302167-8b05dade-c874-40a5-916f-27dc6b61fcbd.PNG)

**[01] number, string, boolean, Date :** ```js let age: number = 19;```

<br/>

**[02] object:** 

```js
const student: {
  name: string;
  age: number;
} = {
  name: 'Jakob',
  age: 19,
}
```

<br/>

**[03] Array:** 

```js
let cars: string[] = ['BMW', 'MARCEDES'] // string-only array
let names: any[] = ['Jakob', 19, 100] // mixed-type array
```

<br/>

**[04] Tuples:**

<p>Fixed length arrays</p>

```js
const role: [number, string]
```

<br/>

**[05] Enums:**

<p>Automatically enumerated global constant identifiers</p>

```ts
enum Role {ADMIN, READ_ONLY, PUBLISHER}
```

**Notes**
- Enum values are automatically assigned values starting from 0
- We can overide this by explicitly setting the first value : `enum Role {ADMIN = 5, READ_ONLY, PUBLISHER}`
- We can set values for all the enums : `enum Role {ADMIN = 5, READ_ONLY = 1000, PUBLISHER= 152}`
- To access them we use the syntax : `Role.ADMIN`, this returns `5`


<br/>

### Downleveling
<p>When we compile the previous example to plain JavaScript we go from</p>

![ts9](https://user-images.githubusercontent.com/77200870/188301981-d0c754d1-c3f8-4a29-a0b7-c6e19ff30d6d.PNG)

To

![ts1](https://user-images.githubusercontent.com/77200870/188301998-515594bc-fb65-474f-836e-652fd69e0f8b.PNG)

>Template strings are a feature from a version of ECMAScript called ECMAScript 2015 (a.k.a. ECMAScript 6, ES2015, ES6, etc. - don’t ask). TypeScript has the ability to rewrite code from newer versions of ECMAScript to older ones such as ECMAScript 3 or ECMAScript 5 (a.k.a. ES3 and ES5). This process of moving from a newer or “higher” version of ECMAScript down to an older or “lower” one is sometimes called downleveling.
By default TypeScript targets ES3, an extremely old version of ECMAScript. We could have chosen something a little bit more recent by using the target option. Running with `--target es2015` changes TypeScript to target ECMAScript 2015, meaning code should be able to run wherever ECMAScript 2015 is supported. So running `tsc --target es2015 hello.ts` gives us the same output above for all es6 features



