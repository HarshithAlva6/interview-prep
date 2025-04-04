Typescript: Statically typed, superset of JS by Microsoft. Address challenges of building large-scale JS applications by adding type annotations, classes, interfaces, namespaces etc.
Type Safety, Backwards Compatibility, Maintainability.
Detecting errors in code without running it is referred to as static checking.
TS vs JS - Optional type annotations vs dynamically typed, syntax, editor integration, type checking, code refactoring. 
TS and JS have interoperability wrt libraries, type definitions (primitive, complex, Type alias, interfaces), can compile TS to JS, type checking using @ts-check comment on top of file at compile time.
npm init, npm i --save-dev typescript (project dependency), tsconfig.json file having compilerOptions. npx tsc to compile TypeScript code.
OR tsc --target ES5 --module commonjs
Running TypeScript - tsc app.ts
Playground - https://www.typescriptlang.org/play
ts-node is TS execution and REPL(Read-Eval-Print Loop) for node.js
Simply run ts-node and you can execute TS script without compiling.
TypeScript types - 
number, string, boolean, any, unknown, void, null, undefined(strictNullChecks), never, object, symbol, enum(auto-increment), Tuple, Array, Union, Intersection, Type Aliases, Type Assertions(as, as const - read only), custom types.
Non-null assertion(!) allows compiler to understand value can't be null or undefined. Satisfies.
Type Inference - Determine type based on value.
Type Compatibility - Regardless of name, compatible as long as structure is same.
Combining types - 
1. Type Union: | helps combine two or more 
2. Intersection Types: & helps create new type by combining multiple existing types.
3. Type Aliases: Create new name for type. type Name = string;
4. keyof operator: Get union of keys from interface/object type.

Type Guards/Narrowing - The type of variable checked using following operators -
1. instanceof: Check if object is instance of class.
2. typeof: Check type of variable to return string.
3. equality: Check the common types in variables.
4. Truthiness: Checking if(strs)
5. Type Predicates: Functions that return boolean value.

TypeScript functions - Function declaration(function name) or function expression(let name = function)
Functions can be declared, arrow, or function type. 
Overloading - Multiple functions with the same name and different parameters.

Typescript interfaces - Define contract for type. Enforce structure for object, class, function argument. Not transpiled to JS, only used by TS at compile-time.
Types vs Interfaces: Types create type based on existing type, while interfaces describe structure of objects and classes.
Extending Interfaces: Using extends
Interface Declaration: With properties, methods as blueprint.
Hybrid Types: Combine multiple types into single type. 