* 不使用webpack
| src
|    - index.js  未显式引入lodash 却使用了_.join
| index.html  需要引入lodash的script文件  同时在body引入index.js文件
| node_modules
| package-lock.json
| package.json
\\ 示例中script标签之间存在隐式依赖关系
  * 使用这种方式管理javascript项目会存在以下问题
   - 无法直接体现，脚本的执行依赖于外部库
   - 如果依赖不存在，或者引入顺序错误，应用程序将无法正常运行
   - 如果依赖被引入但是没有被使用，浏览器将被迫下载无用代码
* 使用webpack
| src
|    - index.js    npm下载lodash import直接引入
| dist
|    - index.html    删除lodash的javascript的引用   将body的script引入改为main.js
| node_modules
| package-lock.json
| package.json

执行 npx webpack 会在dist文件下生成一个 main.js文件