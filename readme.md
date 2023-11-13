# How to deploy to github pages?

https://medium.com/@aishwaryaparab1/deploying-vite-deploying-vite-app-to-github-pages-166fff40ffd3

Step 1: Initialize Git Repository
Run the following commands to initialize a git repository in your Vite app and push your existing code to a remote repository on GitHub.

$ git init
$ git add .
$ git commit -m "initial-commit"
$ git branch -M main
$ git remote add origin http://github.com/{username}/{repo-name}.git
$ git push -u origin main

Step 2: Update vite.config.js
Add the base URL in this file by setting the base as “/{repo-name}/”. For example, if your repository’s name is book-landing-page then set the base like this:



// https://vitejs.dev/config/
export default defineConfig({
  base: "/vite-vanilla-js/"
})


Step 3: Install gh-pages
Install gh-pages package as a dev dependency.

npm install gh-pages --save-dev

Step 4: Update package.json
Update package.json with the following predeploy and deploy scripts.

"scripts": {
    "predeploy" : "npm run build",
    "deploy" : "gh-pages -d dist",
    ...
}
Add the complete website URL by setting homepage in package.json

"homepage": "https://{username}.github.io/{repo-name}/"
Thus, your updated package.json will look like this:

{
  "name": "book-product",
  "private": true,
  "version": "0.0.0",
  "homepage": "https://aishwaryaparab.github.io/book-landing-page/",
  "type": "module",
  "scripts": {
    "predeploy" : "npm run build",
    "deploy" : "gh-pages -d dist",
    "dev": "vite",
    "build": "vite build",
    ...
}
Step 5: Run Deploy
If you’ve made it till here, you’re almost there. Run the final command:

npm run deploy

And you’re done! P.s. packagage.json and vite.config.js and github repozitory name should have the same url, like: vite-vanilla-js