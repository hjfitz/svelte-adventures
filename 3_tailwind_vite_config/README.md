# Adding TaliwindCSS

Import all of your dependencies - configure the plugins in `vite.config.js`. The tricky bit here, if you use ESM, is to make your taliwind config file a `.cjs` file: tailwind appears to use require somewhere in it's import chain. 
