## Node.js 错误
  
#### node-gyp rebuild 错误

有时安装 nodejs 插件时会出现以下错误：

    > node-gyp rebuild


    E:\ArangoDB3e-3.2.1-2_win64\var\lib\arangodb3-apps\_db\arango_gpro\my\gpro\APP\node_modules\nodejieba>if not defined npm_config_node_gyp (node "C:\Program Files\nodejs\node_modules\npm\bin\node-gyp-bin\\..\..\node_modules\node-gyp\bin\node-gyp.js" rebuild )  else (node "" rebuild )
    gyp ERR! configure error
    gyp ERR! stack Error: Can't find Python executable "python", you can set the PYTHON env variable.
    gyp ERR! stack     at failNoPython (C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\configure.js:449:14)
    gyp ERR! stack     at C:\Program Files\nodejs\node_modules\npm\node_modules\node-gyp\lib\configure.js:404:11
    gyp ERR! stack     at C:\Program Files\nodejs\node_modules\npm\node_modules\graceful-fs\polyfills.js:264:29
    gyp ERR! stack     at FSReqWrap.oncomplete (fs.js:123:15)
    gyp ERR! System Windows_NT 6.1.7601
    gyp ERR! command "C:\\Program Files\\nodejs\\node.exe" "C:\\Program Files\\nodejs\\node_modules\\npm\\node_modules\\node-gyp\\bin\\node-gyp.js" "rebuild"
    gyp ERR! cwd E:\ArangoDB3e-3.2.1-2_win64\var\lib\arangodb3-apps\_db\arango_gpro\my\gpro\APP\node_modules\nodejieba
    gyp ERR! node -v v6.10.0
    gyp ERR! node-gyp -v v3.4.0
    gyp ERR! not ok

原因是 node-gyp 安装失败。 node-gyp 用来编译原生C++模块，可能是下载那几个模块的时候 node-gyp 会编译那些模块。

解决方法： 
Windows 下安装以下工具，以管理员的身份启动 powershell，输入以下命令：
    npm --add-python-to-path --python-mirror=https://npm.taobao.org/mirrors/python/ install --global windows-build-tools

node-gyp rebuild 的故障解决办法:      
1 首先清除根目录下的node-gyp  
卸载node-gyp模块   

        npm uninstall node-gyp -g
2 安装环境 

        npm i -g windows-build-tools
重新安装node-gyp

        npm install -g node-gyp
3 设置python版本

        npm iconfig set python python
4 安装.net 2.0 
5 安装vs 201*  c++  环境
6 安装microtime运行时

        npm i microtime --save-dev



#### node-pre-gyp install --fallback-to-build 错误
此时，安装node-gyp

    npm install -g node-gyp
