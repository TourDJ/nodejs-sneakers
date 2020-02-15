## npm 命令
### 查看 npm 包安装根路径
> -g 选项是可选的，不加就是当前项目包的根路径，否则是全局包的根路径  

    npm root [-g]

### 查看/设置 npm 包安装路径前缀

    npm config get prefix
    npm config set prefix path

#### 清除缓存

     npm cache clean --force

### production
添加了 production 参数后将仅仅安装  package.json 中dependencies 里面的包，不会安装 devDependencies 里面的包。

### 查看全局路径

    npm config ls
