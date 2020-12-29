# React Webpack Template &middot; ![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)
This project was created in order that it can be used for different projects, personal, business, you can give it the use you want.
## Available Scripts
To start clone the project and use:
### `npm i `  or you can also use `npm install`

To start the server in your browser:
### `npm run dev`

To create your production files:
### `npm run build`

## What does this template bring?
This template already has installed what is necessary to be able to be used in its entirety
* `ReactJS and ReactDOM`
* `JSX | JS`
* `CSS | SASS`
* `IMG`

### The webpack.config.js is configured as follows:
```js
const path = require('path');
const toml = require('toml');
const yaml = require('yamljs');
const json5 = require('json5');
const { CleanWebpackPlugin } = require('clean-webpack-plugin');
const HtmlWebpackPlugin = require('html-webpack-plugin');

module.exports = {
  entry: './src/index.js',
  output: {
    filename: "js/bundle.[contenthash].js",
    path: path.resolve(__dirname, "dist"),
    publicPath: ""
  },
  mode: 'production',
  module: {
    rules: [
      {
        test: /\.(js|jsx)$/,
        use: 'babel-loader',
        exclude: /node_modules/,
        resolve: {
          extensions: ['.js', '.jsx'],
        },
      },
      {
        test: /\.css$/,
        use: [
            'style-loader', 
            'css-loader'
        ],
      },
      {
        test: /\.(png|jpe?g|gif)$/i,
        use:  [{
            loader: 'file-loader',
            options: {
              name: 'images/[contenthash].[ext]'
            }
        }]
      },
      {
        test: /\.s[ac]ss$/i,
        use: [
            "style-loader",
            "css-loader",
            "sass-loader"
        ],
        resolve: {
            extensions: ['.sass', '.scss']
        }
      },
      { 
        test: /\.txt$/, 
        use: 'raw-loader' 
      },
      {
        test: /\.(woff|woff2|eot|ttf|otf)$/i,
        type: 'asset/resource',
      },
      {
        test: /\.(csv|tsv)$/i,
        use: ['csv-loader'],
      },
      {
        test: /\.xml$/i,
        use: ['xml-loader'],
      },{
        test: /\.toml$/i,
        type: 'json',
        parser: {
          parse: toml.parse,
        },
      },
      {
        test: /\.yaml$/i,
        type: 'json',
        parser: {
          parse: yaml.parse,
        },
      },
      {
        test: /\.json5$/i,
        type: 'json',
        parser: {
          parse: json5.parse,
        },
      }
    ],
  },
  plugins: [
    new CleanWebpackPlugin(),
    new HtmlWebpackPlugin({
      template: './public/index.html',
    }),
  ],
};
```
If you have knowledge of webpack you can modify the exit route to your liking

## About
As explained above, this project has many purposes and if you want to use them in your projects, do not hesitate to do so.

## License
React Webpack Template is [MIT licensed](./LICENSE)
