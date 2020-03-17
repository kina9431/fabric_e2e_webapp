# fabric_e2e_app
本家：https://github.com/sslinml/fabric_e2e_app.git

必要なバージョン:

  ```
  npm 6.4.1
  node.js v8.12.0
  fabric 1.0
  ```
  
  

準備：
  ```
  homebrewをインストール（mac環境なら）
  gitインストール：brew install git
  fabric 1.0インストール：http://www.jeepxie.net/article/758031.html
  
  ```
<h4>手順</h4>

<h4>Step 1:</h4>
 ```
  git clone https://github.com/sslinml/fabric_e2e_app.git
 ```
nodejdkに入る;
  
<h4>Step 2:</h4>

../nodejdk/db.sqlのsql文を沿って、MySQLでデータベースpersonとテーブルpeopleを作る。

MySQL WorkbenchはMySQLの可視化ツール

具体的に：
 ```
MySQLインストール：brew install mysql
MySQLのリモート権限をonにする
データベースのパスワードを変更し、../nodejdk/db.jsonの中身のパスワードを一致とする
 ```
db.sql中身：

```
CREATE DATABASE IF NOT EXISTS person CHARACTER SET utf8;
use person;
CREATE TABLE `people` (
  `name` varchar(32) primary key,
  `password` varchar(32) NOT NULL,
  `department` varchar(64) NOT NULL
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
```
<h4>Step 3:</h4>

現在のパスで以下を実行：
  ```
  npm install
  //遅いかもしれない
  ```
失敗する場合、エラーメッセージに参考し、以下を実行
  ```
  npm audit fix 
  rm -Rf ../node_module
  npm install
  ```

<h4>Step 4:</h4>
  ```
  Fabricネットワークを起動：./startFabric.sh
  権限に問題があれば：chmod a+x startFabric.sh
  もしまた実行できない場合、basic-networkフォルダーに入り、 chmod a+x start.shを実行
  ```

<h4>Step 5:</h4>
   ```
   node registerAdmin.js
   node registerUser.js
   npm start
   ```
   複数回node registerUser.jsを実行したらエラーが出るので、以下を実行する
   ```
   rm -Rf /Users/kina/.hfc-key-store
   再びnode registerAdmin.jsから実行
   
   ```

`http://localhost:3000`に訪問

Errorが出なければ成功
  

<h4>備考：</h4>
もしMySQLとWebの接続がうまくできない場合、Step2で、../nodejdk/package.jsonを開く、

  ```
  最後にpopper.js":"^1.12.9を追加
  npm installを実行
  ```
 
