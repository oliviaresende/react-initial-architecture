# Templete básico para começar uma aplicação React com webpack e babel 

## *Como configurar o ReactJS do zero:* 🚀
1. Ter o **[Node js](https://nodejs.org/en/) instalado** e junto dele a **[Yarn](https://yarnpkg.com/)**;

2. Criar package.json:

```
  yarn init -y
```

3. Adicionar React:

```
  yarn add react react-dom
```

4. Adicionar Babel e Webpack:

```
  yarn add @babel/core @babel/preset-env @babel/preset-react webpack webpack-cli
```

```
  yarn add webpack-dev-server -D
```

5. Criar o arquivo babel.config.js:

```
  module.exports = {
    presets: [
      '@babel/preset-env',
      '@babel/preset-react'
    ]
  }
```

6. Adicionar loaders:

  6.1: Babel

  ```
    yarn add babel-loader
  ```

  6.2 Styles

  ```
    yarn add style-loader css-loader
  ```

  6.3 Images
 
  ```
    yarn add file-loader
  ```

7. Criar pasta public com um arquivo index.html:

```
  `! + enter` para criar a estrutura inicial html
```

  7.1 Adicionar elemento root e script na tag <body>

  ```
    <div id="app"></div>
    <script src="bundle.js"></script>
  ```

8. Criar pasta src com aquivos App.js e index.js:

  8.1 scr/App.js

  ```
    import React from 'react';
 
    function App() {
      return (
        <h1>My app</h1>
      );
    }

    export default App;
  ```

  8.2 src/index.js

  ```
    import React from 'react';
    import {render} from 'react-dom';

    import App from './App';

    render(<App />, document.getElementById('app'));
  ```

9. Criar arquivo webpack.config.js:

```
  const path = require('path');

  module.exports = {
    entry: path.resolve(__dirname, 'src', 'index.js'),
    output: {
      path: path.resolve(__dirname, 'public'),
      filename: 'bundle.js'
    },
    devServer: {
      contentBase: path.resolve(__dirname, 'public'),
    },
    module: {
      rules: [
          {
            test: /\.js$/,
              exclude: /node_modules/,
              use: {
                  loader: 'babel-loader',
              }
          },
          {
            test: /\.css$/,
            exclude: /node_modules/,
            use: [
              { loader: 'style-loader' },
              { loader: 'css-loader' },
            ]
          },
          {
            test: /.*\.(gif|png|jpe?g)$/i,
            use: {
              loader: 'file-loader',
            }
          }
      ]
    }
  }
```
 
10. Criar scripts no package.json

```
  "scripts": {
    "dev": "webpack serve --mode development",
    "build": "webpack --mode production"
  },
```

11. Adicionar plugin para usar async/await:

  11.1 Tranform runtime

  ```
    yarn add @babel/plugin-transform-runtime
  ```

  11.2 Adicionar no babel.config.js

  ```
    plugins: [
      '@babel/plugin-transform-runtime'
    ]
  ```
