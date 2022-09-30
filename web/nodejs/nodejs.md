### Node.js
- 1. 初识Node.js
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
- 2. fs文件系统模块
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
- 3. path路径模块
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
       






















