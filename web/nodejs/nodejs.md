### Node.js
### 1. 初识Node.js
  - 1.1 回顾与思考
    - 浏览器中的javascript运行环境，运行环境是指代码正常运行所需的环境
    - V8引擎负责解析执行javascript代码
    - 内置API是由运行环境提供的特殊接口，只能在所属的运行环境中被调用
  - 1.2 Node.js简介
    - Node.js is a JavaScript runtime built on chrome's V8 JavaScript engine。
    - 1.2.1 Node.js 怎么学习
      - 浏览器中的JavaScript学习路径：
        - JavaScript基础语法 + 浏览器内置API(DOM + BOM) + 第三方库(jquery、art-template等)
      - Node.js的学习路径：
        - JavaScript基础语法 Node.js内置API(fs、path、http等)
        - 第三方API模块(express、mysql等)
  - 1.3Node.js环境的安装
    - 如果希望通过Node.js来运行JavaScript代码，则必须在计算机上安装Node.js环境才行
    - 安装包可以从Node.js的官网首页直接下载
    - 查看已安装的Node.js的版本号
      - 打开终端，在终端输入命令node -v后
### 2. fs文件系统模块
   - 2.1 什么是fs文件模块系统
     - fs模块是Node.js官方提供的用来操作文件的模块。它提供了一系列的方法和属性，用来满足用户对文件操作的需求。
     - 例如：
       - fs.readFile()方法，用来读取指定文件中的内容
       - fs.writeFile()方法，用来向指定文件写入内容
     如果要在JavaScript代码中，使用fs模块来操作文件，则需要使用如下的方式先导入
       ```
       const fs = require('fs')
       ```
   - 2.2 fs.readFile()的语法格式
     - 2.2.1 使用fs.readFile()方法，可以读取指定文件中的内容，语法格式如下：
         ```
         fs.readFile(path[, options], callback)
        参数解读：
        - 参数1： 必须参数，字符串，表示文件的路径
        - 参数2：可选参数，表示以什么编码格式来读取文件
        - 参数3：必须参数，文件读取完成后，通过回调函数拿到读取的结果
         ```
     - 2.2.2 fs.readFile()的示例代码
       - 以utf8的编码格式，读取指定文件的内容，并打印err和dataStr的值：
         ```
         const fs = require('fs')
         fs.readFile('./11.txt','utf8',(err,dataStr) => {
          console.log(err)
          console.log('-----')
          console.log(dataStr)
         })
         ```
   - 2.3 fs.writeFile()的语法格式
     - 2.3.1 使用fs.writeFile()方法，可以向指定的文件中写入内容，语法格式如下：
     ```
      fs.writeFile(file,data[, options], callback)
      参数解读：
      - 参数1：必选参数，需要指定一个文件路径的字符串，表示文件的存放路径
      - 参数2：必须参数，表示要写入的内容
      - 参数3：可选参数，表示以什么格式写入文件内容，默认值是utf8.
      - 参数4：必须参数，文件写入完成后的回调函数
     ```
### 3. path路径模块

    - 3.1 什么是path路径模块
        path模块是Node.js官方提供的、用来处理路径的模块。它提供了一系列的方法和属性，用来满足用户对路径的处理需求。
        - 例如：
          - path.join(),用来将多个路径片段拼接成一个完整的路径字符串
          - path.basename()方法，用来从路径字符串中，将文件名解析出来
          如果要在JavaScript代码中，使用path模块来处理路径，则需要使用如下的方式先导入它：
          ```
          const path = require('path')
          ```
    - 3.2 路径拼接
      - 3.2.1 path.join()的语法格式
      使用path.join()方法，可以把多个路径片段拼接为完整的路径字符串，语法格式如下：
      ```javascript
        path.join([...paths])
        //  参数解读:
        //    ...paths<string> 路径片段的序列
        //    返回值：<string>
      ```
      - 3.2.2 path.join()的代码示例
      ```javascript
        const path = require('path')
        let s = path.join('/a','/b/c','../d','e');
        console.log(s)
        
        //  ..会向上返回一层
        //    打印结果:
        //    \a\b\d\e
        
        const path2 = path.join(__dirname,'./file/1.txt')
        //console.log(path2)//输出 当前文件所处目录
      ```
    - 3.3 获取路径中的文件名
      - 3.3.1 path.basename()的语法格式
      使用path.basename()方法，可以获取路径中的最后部分，经常通过这个方法获取路径中的文件名，语法格式如下：
      ```
        path.basename(path[,ext])
        //参数解读：
        //path<string> 必选参数，表示一个路径的字符串
        //ext<string>可选参数，表示文件扩展名
        //返回：<string>表示路径中的最后一部分
      ```
      - 3.3.2 path.basename()的代码示例
      ```javascript
        const path = require('path')

        let s = path.basename('/a/b/c/d/index.html');
        console.log(s)
        //打印index.html
        let s1 = path.basename('/a/b/c/d/index.html','.html');
        console.log(s1)
        //打印index
      ```
    - 3.4 获取路径中的文件扩展名
      - 3.4.1 path.extname()的语法格式
        使用path.extname()方法，可以获取路径中的扩展名部分，语法格式如下：
        ```
         path.extname(path)
         参数解读：
         - path<string> 必须参数，表示一个路径的字符串
         - 返回：<string> 返回得到的扩展名字符串
        ```
      - 3.4.2 path.extname()代码示例
      ```javascript
        const path = require('path')
        let s = path.extname('/成绩.txt');
        console.log(s)
        //打印.txt

      ```
### 4. http模块
    - 4.1 什么是http模块
      http模块是Node.js官方提供的，用来创建web服务器的模块。通过http模块提供的`http.createServer()`方法。
      就能方便的把一台普通电脑，变成一台Web服务器,从而对外提供Web资源服务。
      如果希望使用http模块创建Web服务器，则需要先导入它：
      
    ```javascript
       const http = require('http')
    ```
### 6. 模块化
    
- 6.1 模块化的基本概念
  - 6.1.1 什么是模块化
    - 模块化是指解决一个复杂问题时，自顶向下逐层把系统划分成若干模块。对整个系统来说，模块是可组成、分解和替换的单元
  - 6.1.2 编程领域的模块化
    - 编程领域的模块化，就是遵守固定的规则，把一个大文件拆成独立并互相依赖的多个小模块。
    - 把代码进行模块化拆分的好处：
      1. 提高了代码的复用性
      2. 提高代码的可维护性
      3. 可以实现按需加载
  - 6.1.3 模块化的规范
    - 6.1.3.1 模块化的规范就是对代码进行模块化的拆分和组合时，需要遵守的那些规则。
    - 例如：
      - 使用什么样的语法格式来引用模块
      - 在模块中使用什么样的语法格式向外暴露成员
    - 6.1.3.2 模块化的好处
      - 大家都遵守相同的模块化规范写代码，降低了沟通的成本。极大方便了各个模块之间的相互调用，利人利己
  - 6.1.4 Node.js中模块的分类
    - Node.js 中根据模块来源的不同，将模块分为了3大类，分别是：
      - 内置模块(内置模块是由Node.js官方提供的，例如fs、path、http等)
      - 自定义模块(用户创建的每个.js文件，都是自定义模块)
      - 第三方模块(由第三方开发出来的模块，并非官方提供的内置模块，也不是用户创建的自定义模块，使用前需要先下载)
  - 6.1.5 加载模块
    - 使用强大的require()方法，可以加载需要的内置模块、用户自定义模块、第三方模块进行使用。例如：
    ```javascript
        //1.加载内置的fs模块
        const fs = require('fs')
        //2.加载自定义模块（可以省略.js后缀）
        const custom = require('./costom.js')
        //3.加载第三方模块
        const moment = require('moment')
    ```
    - ==注意:== 使用require()方法加载其它模块时，会执行被加载模块中的代码  
  - 6.1.6 Node.js中的模块作用域
    - 6.1.6.1 什么是模块作用域
      - 和函数作用域类似，在自定义模块中定义的变量、方法等成员，只能在当前模块内被访问，这种模块级别的访问限制，叫做模块作用域。
      - ```javascript
            //02.test.js
            const custom = require('./01.custom.js')
            //输出{}空对象
            //在02.test.js模块中，无法访问到01.custom.js模块中的私有成员
            console.log(custom)
        ```
      - ```javascript
        //01.custom.js
        //1. 在模块作用域中定义常量 username
        const username = '张三'
        //在模块作用域中定义函数sayHello
        function sayHello(){
            console.log('大家好!我是' + username)
        } 
        ```
    - 6.1.6.2 模块作用域的好处
      - 防止了全局变量的污染问题
      - ```html
            <body>
                <h1>index首页</h1>
                <script src="./reg.js"></script>
                <script src="./login.js"></script>
                <script>
                    console.log(username)
                </script>
            </body>
        ```
        ```javascript
            //reg.js
            var username = '2s'
        ```
        ```javascript
            //login.js
            var username = '1s'
        ```
    - 6.1.6.3 module对象
    - 6.1.6.4 向外共享模块作用域中的成员
      - module.exports对象
      - 在自定义模块中，可以使用module.exports对象，将模块内的成员共享出去，供外界使用。
      - 外界用require()方法导入自定义模块时，得到的就是module.exports所指向的对象
      - ```javascript
            //1.js
            module.exports = {
                user:{
                    username:'snopy'
                },
                sayHello: function (){
                    console.log('hello')
                }
            }
        ```
        ```javascript
            //2.js
            const custom = require('./1.js');
            console.log(custom)
            //打印
            // { user: { username: 'snopy' }, sayHello: [Function: sayHello] }
            
        ```
      - 共享成员时的注意点
        - 使用require()方法导入模块时，导入的结果，永远以module.exports指向的对象为准
        - ```javascript
            //1.js
            module.exports.username = 'snopy';
            module.exports.sayHello = function() {
                console.log('hellos')
            }
            //让module.exports指向一个全新的对象
            module.exports = {
                nickname:'小黑',
                sayHi: function() {
                    console.log('Hi')
                }
            }
          ```
          ```javascript
            //1.引入1.js
            const custom = require('./1.js');
            console.log(custom)
            //引入的对象只有新指向的对象
            //{ username: '小黑', sayHi: [Function: sayHi] }
          ```
      - exports对象
        - 由于module.exports单词写起来比较复杂，为了简化向外共享成员的代码，Node提供了exports对象。
        - 默认情况下，exports和module.exports指向同一个对象。最终共享的结果，还是以module.exports指向的对象为准。
        - ```javascript
            //1.js 
            console.log(module.exports)
            console.log(exports)
            console.log(module.exports === exports)       
            //{}
            //{}  
            //true
          ```
      - exports和module.exports的使用误区
        - 时刻谨记，使用require()模块时，得到的永远是module.exports指向的对象
        - 为了防止混乱，建议不要在同一个模块中同时使用exports和module.exports
        
- 6.2 CommonJS规范
  - Node.js遵循CommonJS模块化规范，CommonJS规定了模块的特性和各模块之间如何相互依赖。
  - CommonJS规范
    1. 每个模块内部，module变量代表当前模块
    2. module变量是一个对象，它的exports属性(module.exports)是对外的接口
    3. 加载某个模块，其实就是加载该模块的module.exports属性。require()方法用于加载模块。

- 6.3 Node.js中模块的三大分类各自是什么
- 6.4 使用npm管理包
- 6.5 规范的包结构
- 6.6 模块的加载机制


















