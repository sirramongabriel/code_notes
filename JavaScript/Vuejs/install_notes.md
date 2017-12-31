## Vue.js + Framework7 Install

1. Install Framework7
 
   There are few ways to install Framework7:

    - Download it from [Framework7 GitHub repository](https://github.com/framework7io/framework7/releases)

    - Using NPM: ```$ npm install framework7```

    - Using Bower: ```$ bower install framework7```

2. Install Vue
 
  There are a few ways to install Vue.js:
  
    - Direct ```<script>``` Include

        - Simply [download](https://vuejs.org/v2/guide/installation.html) and include with a script tag. Vue will be registered as a global variable.

        - Don’t use the minified version during development. You will miss out on all the nice warnings for common mistakes!

    - CDN
        - Recommended: [This CDN Link](https://cdn.jsdelivr.net/npm/vue), which will reflect the latest version as soon as it is published to npm.
        
    - NPM 
    The recommended installation method when building large-scale apps with Vue. It pairs nicely with module bundlers such as [Webpack](https://webpack.js.org/) or [Browserify](http://browserify.org/). Vue also provides accompanying tools for authoring [Single File Components](https://vuejs.org/v2/guide/single-file-components.html).

    ```javascript
    // latest stable
    npm install vue
    ```
    
    - CLI 
    Vue.js provides an [official CLI](https://github.com/vuejs/vue-cli) for quickly scaffolding ambitious Single Page Applications. It provides batteries-included build setups for a modern frontend workflow. It takes only a few minutes to get up and running with hot-reload, lint-on-save, and production-ready builds:
    
    ```javascript 
    // install vue-cli
    npm install --global (or -g) vue-cli
    // create a new project using the 'webpack'template
    vue init webpack my-prpoject
    // install dependencies and start building!
    cd my-project
    npm install
    // start development server
    npm run dev
    ```
    

    