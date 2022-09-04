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

### Everday Types
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

**[01] number, string, boolean, Date :**

```ts 
let age: number = 19;
```

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

> The type part of each property is optional, if it's not specified it's assumed to be of type `any`

> We can set a property to be optional by using ? : `obj: { first: string; last?: string }`

<p>In JavaScript, if you access a property that doesn’t exist, you’ll get the value `undefined` rather than a runtime error. Because of this, when you read from an optional property, you’ll have to check for `undefined` before using it.</p>

![ts7](https://user-images.githubusercontent.com/77200870/188303248-50369664-19a9-4736-b26e-c1dd14ae8d76.PNG)

<br/>

**[03] Arrays:** 

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

**[05] Enums:**

```ts
let addValues: Function;
```
<br/>

### Downleveling
<p>When we compile the previous example to plain JavaScript we go from</p>

![ts9](https://user-images.githubusercontent.com/77200870/188301981-d0c754d1-c3f8-4a29-a0b7-c6e19ff30d6d.PNG)

To

![ts1](https://user-images.githubusercontent.com/77200870/188301998-515594bc-fb65-474f-836e-652fd69e0f8b.PNG)

>Template strings are a feature from a version of ECMAScript called ECMAScript 2015 (a.k.a. ECMAScript 6, ES2015, ES6, etc. - don’t ask). TypeScript has the ability to rewrite code from newer versions of ECMAScript to older ones such as ECMAScript 3 or ECMAScript 5 (a.k.a. ES3 and ES5). This process of moving from a newer or “higher” version of ECMAScript down to an older or “lower” one is sometimes called downleveling.
By default TypeScript targets ES3, an extremely old version of ECMAScript. We could have chosen something a little bit more recent by using the target option. Running with `--target es2015` changes TypeScript to target ECMAScript 2015, meaning code should be able to run wherever ECMAScript 2015 is supported. So running `tsc --target es2015 hello.ts` gives us the same output above for all es6 features


<br/>

### Functions
#### Parameter Type Annotations

<p>When you declare a function, you can add type annotations after each parameter to declare what types of parameters the function accepts. Parameter type annotations go after the parameter name:</p>

![ts](https://user-images.githubusercontent.com/77200870/188305088-a282e66d-52f0-4e57-871b-6b1a5399c9ae.PNG)

<p>When a parameter has a type annotation, arguments to that function will be checked</p>

![ts1](https://user-images.githubusercontent.com/77200870/188305120-7c7ec750-f18a-49c5-9174-23549a09186e.PNG)

>Even if you don’t have type annotations on your parameters, TypeScript will still check that you passed the right number of arguments.

#### Return Type Annotations

<p>You can also add return type annotations. Return type annotations appear after the parameter list:</p>

![ts5](https://user-images.githubusercontent.com/77200870/188305151-82e1c43d-02d0-4c9c-a828-80f4e82a915a.PNG)

**Note** 🚧
>Much like variable type annotations, you usually don’t need a return type annotation because TypeScript will infer the function’s return type based on its return statements. The type annotation in the above example doesn’t change anything. Some codebases will explicitly specify a return type for documentation purposes, to prevent accidental changes, or just for personal preference.

<br/>

### Union Types

<p>TypeScript’s type system allows you to build new types out of existing ones using a large variety of operators. Now that we know how to write a few types, it’s time to start combining them in interesting ways.</p>

#### Defining a Union Type

<p>The first way to combine types you might see is a union type. A union type is a type formed from two or more other types, representing values that may be any one of those types. We refer to each of these types as the union’s members.
Let’s write a function that can operate on strings or numbers:</p>

![ts2](https://user-images.githubusercontent.com/77200870/188302845-31421fe3-f18b-4482-8c63-9295099890c6.PNG)

#### Working with Union Types
> TypeScript will only allow an operation if it is valid for every member of the union. For example, if you have the union string | number, you can’t use methods that are only available on string

![ts3](https://user-images.githubusercontent.com/77200870/188302912-815d6e0f-c8a7-493f-b119-8dfd847821c9.PNG)

<p>The solution is to narrow the union with code, the same as you would in JavaScript without type annotations. Narrowing occurs when TypeScript can deduce a more specific type for a value based on the structure of the code.
For example, TypeScript knows that only a string value will have a typeof value "string":</p>

![ts4](https://user-images.githubusercontent.com/77200870/188302940-0a50e18b-84ba-45fb-8f6f-62a521aba5f0.PNG)

<p>Another example is to use a function like Array.isArray:</p>

![ts5](https://user-images.githubusercontent.com/77200870/188302970-b10d19a2-073b-438d-80a3-7dd3390d7b32.PNG)

>Notice that in the else branch, we don’t need to do anything special - if x wasn’t a string[], then it must have been a string.

<p>Sometimes you’ll have a union where all the members have something in common. For example, both arrays and strings have a slice method. If every member in a union has a property in common, you can use that property without narrowing:</p>

![ts6](https://user-images.githubusercontent.com/77200870/188303024-a4991a52-632e-4423-b7d5-ce035356d2cb.PNG)

<br/>

### Literal Types

![ts8](https://user-images.githubusercontent.com/77200870/188303475-55407fa6-356b-413f-baac-d2294fbcd269.PNG)

<p>By themselves, literal types aren’t very valuable:</p>

![ts9](https://user-images.githubusercontent.com/77200870/188303494-6781b6d0-cea5-4b82-af33-89cda7b842f6.PNG)

<p>It’s not much use to have a variable that can only have one value!</p>

<p>But by combining literals into unions, you can express a much more useful concept - for example, functions that only accept a certain set of known values:</p>

![ts](https://user-images.githubusercontent.com/77200870/188303594-8a132a83-0fd3-4cd9-9bd7-c17036953e84.PNG)

<p>Numeric literal types work the same way:</p>

![ts1](https://user-images.githubusercontent.com/77200870/188303598-54b2d213-f6c2-4cef-a73d-204cbb32e6eb.PNG)

<p>Of course, you can combine these with non-literal types:</p>

![ts2](https://user-images.githubusercontent.com/77200870/188303627-f06c011b-8105-496b-8cab-46cf33d79caf.PNG)

<br/>

### Type Aliases
<p>We’ve been using object types and union types by writing them directly in type annotations. This is convenient, but it’s common to want to use the same type more than once and refer to it by a single name.</p>

```ts
type ID = number | string;

type ReturnType = "as-text" | "as-number"
```

<p>And for objec</p>

![ts3](https://user-images.githubusercontent.com/77200870/188304193-73b58446-149a-4a0e-a923-94fcd8aa154b.PNG)

<br/>

### Functions as Types
<p>The simplest way to describe a function is with a function type expression. These types are syntactically similar to arrow functions:</p>

![ts8](https://user-images.githubusercontent.com/77200870/188306772-b4472a27-f0bf-4100-81f5-0181a08a9d19.PNG)

>The syntax `(a: string) => void` means “a function with one parameter, named a, of type string, that doesn’t have a return value”. Just like with function declarations, if a parameter type isn’t specified, it’s implicitly `any`.

> Note that the parameter name is required. The function type (string) => void means “a function with a parameter named string of type any“!

<p>Of course, we can use a type alias to name a function type:</p>

![ts7](https://user-images.githubusercontent.com/77200870/188306694-69a61d2f-64a3-484c-aaa4-7ab921399f0a.PNG)

### **Other Types to Know About**
#### unknown
<p>The unknown type represents any value. This is similar to the any type, but is safer because it’s not legal to do anything with an unknown value:</p>

![ts9](https://user-images.githubusercontent.com/77200870/188307405-c9bcd1e3-743f-4339-bd12-f96b91efca1d.PNG)

```ts
let userInput: unkown;
let userName: string;

userInput = 5;
userInput = 'Max'

if (typeof userInput === 'string') {
  userName = userInput;
}
```





