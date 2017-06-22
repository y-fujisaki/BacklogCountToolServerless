# BacklogCountTool:Serverless Framework version
## 概要
backlogの、当月1ヶ月分のチケット総数、予定時間、実績時間を集計し、Slackへ通知するLambda Functionです。
Serverless Frameworkが実行可能であること前提となります。


## リポジトリのclone
```
git clone https://github.com/y-fujisaki/BacklogCountToolServerless.git
```


## serverless-python-requirementsインストール
* PGで必要なPythonパッケージリスト(requirements.txt)をデプロイ時のパッケージに含めるプラグイン

```
npm install --save serverless-python-requirements
```

## config.pyの変更
ご利用の環境に合わせて値を入力してください。

``` config.py
## ホスト名
host = '{your-space}' 
## Backlog API KEY
api = '{your-apikey}'
## MEMBER名とIDを指定：集計する担当者分セット
assigend_member=[['name1',{担当者のID}],['name2',{担当者のID}]]
## Slack Webhook
slack_webhook="your-slack-Webhook URL"
```

## Serverless Frameworkでデプロイ
```
# デプロイ
sls deploy -v 

# 作成されたLambda関数を実行
sls invoke -f backlog
```

## イメージ（Slack通知）
![サンプル](https://s3-ap-northeast-1.amazonaws.com/backlog-count-tool/image.png "サンプル")

## Serverless Framework環境構築参考HP

http://dev.classmethod.jp/cloud/aws/easy-deploy-of-lambda-with-serverless-framework/
