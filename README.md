# 初始化`electron-vue`

1. `vue init simulatedgreg/electron-vue my-app`

2. `yarn install`

3. 替换`src/index.ejs`内容

   ```html
   <!DOCTYPE html>
   <html>
   
   <head>
     <meta charset="utf-8">
     <title>vest</title>
     <% if (htmlWebpackPlugin.options.nodeModules) { %>
     <!-- Add `node_modules/` to global paths so `require` works properly in development -->
     <script>
       require('module').globalPaths.push('<%= htmlWebpackPlugin.options.nodeModules.replace(/\\/g, '\\\\') %>')
     </script>
     <% } %>
   </head>
   
   <body>
     <div id="app"></div>
     <!-- Set `__static` path to static files in production -->
     <%  if (!require('process').browser) { %>
     <script>
       if (process.env.NODE_ENV !== 'development') window.__static = require('path').join(__dirname, '/static').replace(/\\/g, '\\\\')
     </script>
     <% } %>
   
     <!-- webpack builds are automatically injected -->
   </body>
   
   </html>
   ```

4. 在`src/renderer/main.js`中添加

   `process.env['ELECTRON_DISABLE_SECURITY_WARNINGS'] = 'true'`

   清除不必要的警告

## 使用`element-ui`



1. 安装

   ```shell
   npm i element-ui -S
   ```

2. 在`main.js`中添加

   ```js
   import ElementUI from "element-ui";
   import "element-ui/lib/theme-chalk/index.css";
   
   Vue.use(ElementUI);
   ```

   

3. 将`element-ui`添加到白名单

   在`.electron-vue/webpack.renderer.config.j`中给`whiteListedModules`添加`element-ui`字段

