# Deno JS

  Deno is built on **Rust**

* Deno is runtime environment like node JS

* Deno supports Typescript

* ES6 syntax and ES6 features are suported

  ```js
  import something from 'somethings'; 
  ```

  not as

  ```js
  const http = require('http');
  ```

* No need of node modules and npm to install and manage packages.Deno directly uses dependencies from web server

  > Downloads the dependencies for the first time.In future usages it will access the dependencies from the cache it stored before

  

  ```js
  import { serve } from 'https://deno.land/std@0.50.0/http/server.ts';
  ```

* Able to use await in plain vanila also with asycn functions

* It is a secure run time environment. It means that node js have no security by default. If we use third party packages, it can able to read, write, access files and network of the system. But Deno allows third layer security and allows only those permissions which are mentioned by the developer

     ```js
// running deno
deno run deno.ts ====> deno run <fileName>.<js || ts>
// running deno with permissions
deno run --allow-net deno.ts
     ```

