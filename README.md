# iOS_Flutter_Hybrid_Project
搭建 iOS Native Flutter 混合工程 步骤

#### 操作步骤：
1. 创建flutter项目
   使用`flutter create -t module my_flutter`创建 Flutter Module 工程。
   
2. 拷贝相关文件
   下载项目 [iOS_Flutter_Hybrid_Project](https://github.com/CaffreySun/iOS_Flutter_Hybrid_Project)
   复制"Script/Maven/Flutter"目录内的所有文件到 Flutter Module 工程根目录.
   复制"Script/Maven/Native"中出Podfile外的文件到 Native 根目录。
   复制"Script/Maven/Native/Podfile"文件内 "end" 后面的配置内容到自己 Native 工程的 Podfile。并根据自己的工程修改配置。
   
3. 修改脚本build_ios.sh，将本项目中的build_ios.sh内容拷贝过去。
   
4. 在Native工程执行 `pod install`

#### 其他操作
1. 给项目配置单独的Flutter SDK,以防和团体合作中各自本地电脑的flutter SDK发送冲突
   借用[flutter_wrapper](https://juejin.im/post/5c3ae5ef518825242165c5ca)工具
      * 进入 Flutter 工程目录安装 'flutter_wrapper'，
      执行 `sh -c "$(curl -fsSL https://raw.githubusercontent.com/passsy/flutter_wrapper/master/install.sh)"`
      * 此后在当前 Flutter 工程需要使用 flutter 命令的地方都使用 ./flutterw来代替

2. 自定义插件
   Flutter package包括两种类型： Dart packages（Dart包）  和 Plugin packages（插件包）
   * 插件包的创建
   命令 `flutter create --template=plugin hello` 
   或者  `flutter create --org com.example  --template=plugin hello` 其中  com.example为包名
   * 插件包的引入，参考：
   ```
   nativefetch:
     path: ./plugins/nativefetch  
   ```
   注意以上的格式，path缩进2个空格


#### 热重载
   创建flutter项目
   debug 模式下可以使用热重载对flutter进行调试和开发，可使用如下命令
     
   `.flutter/bin/flutter attach --debug-port=xxxx`
   安装了flutter_wrapper也可以使用
   `./flutterw attach --debug-port=xxxx`
   xxxx 为端口号
