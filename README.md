# Steps to reproduce

1. Create a project directory (say `node_express`), and `cd` into that folder (like `cd node_express`).
2. Run `npm init -y` to get a starter `package.json` file.
3. In the `package.json` file,
   a. Add this key-value pair: `"type" : "module"`. Don't forget the comma after "module". 
   b. In "scripts", remove any existing key-value pairs. Then add this key-value pair: `"dev": "nodemon index.js"`.
4. Create a file named `index.js`
5. You will need the following packages: express, nodemon, dotenv. Install them using `npm i express nodemon dotenv`.
6. To run the app, you can use the `dev` script we added earlier. Type this command: `npm run dev`. This will run `index.js` using `nodemon`, which is not a necessity but it helpful as whenever you save any file in the project, `nodemon` automatically restarts the server.
7. Because of the `"type": "module"` change in `package.json`, instead of `const express = require("express")`, which is old-syntax, you can use `import express from "express"`, and so on for other imports. Note that this is not an optional syntax anymore, meaning if you try the old-syntax with `"type": "module"`, your server will throw an error.
8. Create a blank `.env` file. Leave it empty for now.
9. Create a `.gitignore` file. It should have the following contents:
   - `.env`. There are some secrets like API keys and database connection strings, which if compromised can allow unauthorised access to your database/API service. To avoid such scenarios, first we need to make sure our repo is private. Then for added safety, we store these secrets in this `.env` file. Then we include this file in our `.gitignore` file so that it is not pushed to the repo, so even if someone gains access to the repo somehow, they can't access these secrets.
   - `node_modules`. The `node_modules` folder contains the installed packages, and thus can grow in size upto several GBs. Since the list of packages needed for the project are already given in `package.json`, one can install these packages using `npm i`, and so does not need the `node_modules` folder, and hence it should be ignored by git.
   - `package-lock.json`. When you run `npm i`, a temporary file namely `package-lock.json` is created, which should be ignored by git. I use `pnpm` instead of `npm`, so I also have to include `pnpm-lock.yaml` in the `.gitignore` file.
10. Now, you are ready to start working on your backend project.