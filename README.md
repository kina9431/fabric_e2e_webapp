# fabric_e2e_app
原作者：https://github.com/sslinml/fabric_e2e_app.git

库版本:

  ```
  npm 6.4.1
  node.js v8.12.0
  fabric 1.0
  ```
  
  版本一定要是上列版本
  
  
  下载homebrew
  下载
<h4>安装及配置</h4>

Step 1:
 ```
  git clone https://github.com/sslinml/fabric_e2e_app.git
 ```
进入nodejdk目录下;
  
Step 2:
在nodejdk目录下找到db.sql,按照里面的sql语句在MySQL中创建`person` DATABASE以及TABLE `people`

可装MySQL Workbench进行可视化操作

操作：
 ```
brew install mysql
设置remote权限
修改密码，并修改nodejdk目录下的db.json文件中的密码，保持一致
 ```
执行下列sql：

```
CREATE DATABASE IF NOT EXISTS person CHARACTER SET utf8;
use person;
CREATE TABLE `people` (
  `name` varchar(32) primary key,
  `password` varchar(32) NOT NULL,
  `department` varchar(64) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
Step 3:
当前目录执行以下命令：
  ```
  npm install
  //安装时速度可能会很慢，静等即可
  ```
如安装不成功，根据提示执行
  ```
  npm audit fix 
  rm -Rf ../node_module
  npm install
  ```

Step 4:
  ```
  ./startFabric.sh
  若遇到权限问题执行chmod a+x startFabric.sh
  若仍有问题进入basic-network文件夹下执行 chmod a+x start.sh
  ```

Step 5:
   ```
   node registerAdmin.js
   node registerUser.js
   npm start
   ```
   多次执行node registerUser.js会出错，需要执行以下命令删掉，
   ```
   rm -Rf /Users/kina/.hfc-key-store
   再重新从node registerAdmin.js开始执行
   
   ```

访问`http://localhost:3000`
  如不出Error即访问成功
  


如有Error,可在Step2中，nodejdk文件夹中修改package.json最后一行加入
  ```
  popper.js":"^1.12.9
  然后执行 npm install
  ```
 
