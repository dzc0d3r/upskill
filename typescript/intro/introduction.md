## Introduction to TypeScript

### What is TypeScript? 
To answer this question let's refer to [the official typescript language website](https://www.typescriptlang.org/). According to the website TypeScript is described as JavaScript with syntax for types, a strongly typed programming language that builds on JavaScript, giving you better tooling at any scale. 
Meaning it's an extension and a superset of JavaScript which is developed and maintained by Microsoft as an open-source programming language.

### Why TypeScript?  
While JavaScript is powerful, its lack of static typing can lead to unexpected behavior and makes it challenging to maintain larger projects. TypeScript addresses these issues by introducing optional static typing, enabling developers to catch errors early in the development process.

JavaScript's peculiar behaviors, such as type coercion and implicit type conversion, can sometimes lead to bugs that are difficult to detect. With TypeScript, developers can define types for variables, function parameters, and return values, making code more predictable and easier to understand.

Moreover, TypeScript supports features like interfaces, enums, classes, and modules, which are absent or less robust in plain JavaScript. These language features help developers write cleaner and more maintainable code, especially in complex applications.

One of the key benefits of TypeScript is its compatibility with existing JavaScript codebases. Since TypeScript code is transpiled into plain JavaScript, it can seamlessly integrate with JavaScript libraries and frameworks, allowing developers to gradually introduce TypeScript into their projects without requiring a complete rewrite.

### What i need to start writing TypeScript? 
In order to start writing typescipt you to: 
1. Install typescript first on your machine, while you can use multiple package managers like `apt` or `pacman` to do so. The easiest recommended way is to use `npm` :
```bash
npm install -g typescript
```
2. A code editor like nvim, or vscode. 
3. [OPTIONAL] Install `tsx` to run typescript directly from node: 
```bash
npm install -g tsx 
```
### Your first TypeScript Programm 
1. In your favorite code editor create a file named `app.tsx` for e.g with the following content: 
```typescript 
let username = "Walid"
console.log(`Hello ${username}`)
```
2. Open your terminal and run :
```bash 
tsc app.ts
```
This will compile `app.ts` and produce a `app.js` file in the same directory which you can run :
```bash 
node app.js
```
Output: 
```bash 
Hello Walid!
``` 
[OPTIONAL] if you installed `tsx` use the following to produce the sameoutput without the need to compile the file : 
```bash
tsx app.ts
```
#### BONUS 
Try to rename the `username` variable to name, and try to run:
```bash
tsc app.ts
```
And then

```bash
tsx app.ts
```
You will be surprised that `tsc` will error while `tsx` will run smoothly
##### Explaination 
1. The reason why tsc errored is because typescript by default includes type checking `.d.ts` files like `lib.dom.d.ts` which caused the error and since we're not using any `tsconfig.json` to skip the lib check we got the previous error that's because `name` was also declared in typescript `lib.dom.d.ts`.
To fix this create a `tsconfig.json` by runing: 
```bash
tsc --init 
```
notice in the output `skipLibCheck: true`, this will skip type checking all `.d.ts` files including the typescript ones (to disable only those see : "skipDefaultLibCheck": true in tsconfig.json) 
then run:
```bash
tsc app.ts
```
this time typescript will not complain. 

2. `tsx` didn't error that's because tsx execute only the code in `app.ts` and that's all.  
