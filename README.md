# ViteR
基于vite创建的react仓库
参考https://juejin.cn/post/7213575951116058685

## 仓库创建
1. `yarn create vite`
2. 选择React + TS
3. 如果需要更换端口的话： 配置启动端口vite --port=8888
4. 如果需要：更改了根文件路径，引入path包`yarn add @types/node -D`
5. 如果需要ESlint 则`yarn create @eslint/config`

## ESLint + Prettier
### ESlint 检查
```javascript
// package.json
"sricpts": {
  // ...
  "lint": "eslint src --ext .vue,.js,.ts,.jsx,.tsx --fix"
}
// 同时需要我们在 .eslintrc.cjs 加上一个 extends 配置 "plugin:react/jsx-runtime"。
```

#### 使用hook写法需注意
1. 安装`yarn add eslint-plugin-react-hooks -D`
2. 在.eslintrc.cjs的 extends 和plugins 分别加上"plugin:react-hooks/recommended"和"react-hooks"

### 添加格式化prettier
1.`yarn add prettier -D`
2. 根目录创建 .prettierrc文件
3. 写入如下，具体配置查询文档
   ```js
   {
      "semi": false,
      "singleQuote": false,
      "printWidth": 90,
      "useTabs": false,
      "tabWidth": 2,
      "bracketSpacing": true
    }
   ```
4. 根目录创建 .prettierignore 配置文件
5. 写入如下，具体配置查询文档
   ```js
   .DS_Store
    node_modules
    dist
    dist-ssr

    **/*.svg
    **/*.sh
   ```
### 结合ESLint和Prettier
1. yarn add eslint-config-prettier eslint-plugin-prettier -D
2. 修改.eslintrc.cjs文件

### 添加 husky 和 lint-staged
1. `yarn add husky lint-staged -D`
2. 执行以下命令会生成 .husky 文件`npx husky install 和npx husky add .husky/pre-commit "npx lint-staged"`
3. 在package.json添加
   ```js
    "lint-staged": {
      "*.{vue,ts,js,jsx,tsx}": [
      "yarn lint"
      ]
    }
    ```
## vite.config.ts 配置
1. `yarn add vite-plugin-eslint -D`
2. 引入这个包，并在plugins配置
  ```js
    viteEslint({
        failOnError: false,
    }),
  ```