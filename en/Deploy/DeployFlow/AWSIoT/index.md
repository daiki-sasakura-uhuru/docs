---
lastUpdated: 2017-12-01
WIP: true
---

# AWS IoT へのデプロイ

enebular では作成した Flow を AWS IoT にも書き出すことができます。

## Flow の作成

今回は以下のような Flow を作成します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_02.png)

フローが出来たら Export to Other Services を押します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_03.png)

Deployment Flowが表示されることを確認します。

![](https://i.gyazo.com/925d997c94f95f0e1f96f76b511621f3.png)


## AWS IoT で設定を作成

AWS IoT で今回用の設定を作成します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_05.png)

メニューから 登録＞モノ を選択します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_06.png)

モノの登録は好きな名前をつけます。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_07.png)

モノの作成を押します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_08.png)

シャドウを確認します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_09.png)

証明書を作成します。

## 証明書を作成

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_10.png)

鍵ファイルを全てダウンロードして有効化します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_11.png)

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_12.png)

ポリシーのアタッチを押します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_13.png)

新規ポリシーの作成を押します。

## 新規ポリシーの作成

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_14.png)

名前はわかりやすい名前を指定します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_15.png)

つづいて、ステートメントを追加します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_16.png)

ポリシー構文は以下のように指定します。

* アクション
    * iot:*
* リソース ARN
    * *

このポリシー構文は一旦試すための許可範囲が広い設定です。慣れてきたら、ポリシーも細かく調整してみてください。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_17.png)

作成ボタンを押してポリシーを保存します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_18.png)

このままだとポリシーと証明書が結びついてないのでアタッチします。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_19.png)

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_20.png)

## フローにAWS IoTの設定を反映

先ほどのAWS IoT設定画面に戻りフローにAWS IoTの設定を反映します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_21.png)

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_22.png)

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_23.png)

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_24.png)

（アクセスキーを設定した画像）
![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_24.png)

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_25.png)

## agentのインストール

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_26.png)

<a href="https://github.com/enebular/enebular-awsiot-agent" target="_blank">GitHub</a>からダウンロードしてきます。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_27.png)

exampleフォルダに移動します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_28.png)

コマンドを実行します。

![image](/_asset/images/Deploy/DeployFlow/AWSIoT/deploy-deployflow-awsiot_29.png)

```
windows

set AWSIOT_CONFIG_FILE=./config.json
set NODE_RED_DIR=./node-red
node_modules\.bin\enebular-awsiot-agent
```