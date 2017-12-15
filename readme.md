
Step 1 - Create the Root Folder

The root folder will be named reactApp and we will place it on Desktop. After the folder is created, we need to open it and create empty package.json file inside by running npm init from the command prompt and follow the instructions.

C:\Users\username\Desktop>mkdir reactApp
C:\Users\username\Desktop\reactApp>npm init

Step 2 - Install Global Packages
We will need to install several packages for this setup. We will need some of the babel plugins, so let's first install babel by running the following code in the command prompt window.

C:\Users\username\Desktop\reactApp>npm install -g babel
C:\Users\username\Desktop\reactApp>npm install -g babel-cli

Step 3 - Add Dependencies and Plugins
We will use webpack bundler in these tutorial. Let's install webpack and webpack-dev-server.

C:\Users\username\Desktop\reactApp>npm install webpack --save
C:\Users\username\Desktop\reactApp>npm install webpack-dev-server --save
Since we want to use React, we need to install it first. The --save command will add these packages to package.json file.

C:\Users\username\Desktop\reactApp>npm install react --save
C:\Users\username\Desktop\reactApp>npm install react-dom --save
As already mentioned, we will need some babel plugins, so let's install it too.

C:\Users\username\Desktop\reactApp>npm install babel-core
C:\Users\username\Desktop\reactApp>npm install babel-loader
C:\Users\username\Desktop\reactApp>npm install babel-preset-react
C:\Users\username\Desktop\reactApp>npm install babel-preset-es2015

Step 4 - Create the Files
Let's create several files that we need. It can be added manually or using the command prompt.

C:\Users\username\Desktop\reactApp>touch index.html
C:\Users\username\Desktop\reactApp>touch App.jsx
C:\Users\username\Desktop\reactApp>touch main.js
C:\Users\username\Desktop\reactApp>touch webpack.config.js
Alternative way to create files that we need

C:\Users\username\Desktop\reactApp>type nul >index.html
C:\Users\username\Desktop\reactApp>type nul >App.jsx
C:\Users\username\Desktop\reactApp>type nul >main.js
C:\Users\username\Desktop\reactApp>type nul >webpack.config.js

Step 5 - Set Compiler, Server and Loaders
Open webpack.config.js file and add the following code. We are setting webpack entry point to be main.js. Output path is the place where bundled app will be served. We are also setting the development server to 8080 port. You can choose any port you want.

And lastly, we are setting babel loaders to search for js files, and use es2015 and react presets that we installed before.

webpack.config.js
var config = {
   entry: './main.js',
   output: {
      path:'/',
      filename: 'index.js',
   },
   devServer: {
      inline: true,
      port: 8080
   },
   module: {
      loaders: [
         {
            test: /\.jsx?$/,
            exclude: /node_modules/,
            loader: 'babel-loader',
            query: {
               presets: ['es2015', 'react']
            }
         }
      ]
   }
}
module.exports = config;
Open the package.json and delete "test" "echo \"Error: no test specified\" && exit 1" inside "scripts" object. We are deleting this line since we will not do any testing in this tutorial. Let's add the start command instead.

"start": "webpack-dev-server --hot"

Before the above step, it will required webpack-dev-server. To install webpack-dev-server, use the following command.

C:\Users\username\Desktop\reactApp>npm install webpack-dev-server -g