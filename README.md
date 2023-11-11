# AWS-CLI-CloudFormation
AWS CLIを利用してCloudFormationスタック作成を行います。今回は**無料枠でVPC作成**、**リソースを使用せず**に作成していきます。<br>

1. **AWS CLIのセットアップ**
   1. AWS公式サイトからCLIをインストール
   1. `` aws --version``を実行して、CLIがインストールされているか確認します<br>
無事確認できました。``aws-cli/2.13.33 Python/3.11.6 Darwin/21.6.0 exe/x86_64 prompt/off``
   1. `aws configure`をコマンドラインで実行して、**アクセスキーID**、**シークレットアクセスキー**、<br>**デフォルトリージョンの設定**、**出力フォーマットの設定**を行います。<br>
   <br>下記のセキュリティ認証情報から確認します。<br>
   <img width="600" alt="スクリーンショット 2023-11-10 20 24 26" src="https://github.com/Kana-Karin/AWS-CLI-CloudFormation/assets/84316229/18dc7c78-bf11-40d0-8919-4b7fc3c4064d"> <br>
   
``` AWS Access Key ID [None]: アクセスキーIDを入力
AWS Secret Access Key [None]: シークレットキーを入力
Default region name [None]: リージョンを入力
Default output format [None]: 出力フォーマットを入力
```
出力フォーマットにはjson,text,tableが選択できます。<br>S3やDBを使用する際、可読性が高いのはtableフォーマットらしいので、今回はtableを指定します。<br>
``cat ~/.aws/credentials``を利用して確認します。<br>
<img width="300" alt="スクリーンショット 2023-11-10 21 18 04" src="https://github.com/Kana-Karin/AWS-CLI-CloudFormation/assets/84316229/5106d922-9ada-44e2-91b0-df02b221d268">

2. **CloudFormationテンプレートの準備、作成**<br>
   今回は、**my-stack**, **mytemplate.yaml**でスタックを作成します。<br>
   ``file://``には.yamlファイルがあるディレクトリを指定します。<br>
   ``aws cloudformation create-stack --stack-name my-stack --template-body file://./aws-cloudformation/mytemplate.yaml``<br>
<img width="４34" alt="スクリーンショット 2023-11-11 16 25 22" src="https://github.com/Kana-Karin/AWS-CLI-CloudFormation/assets/84316229/e107e16b-4611-4767-a2f5-0b217648636c"><br>
スタックがcreateされました。

4. **実際にコンソール画面に行って確認**<br>
   <img width="400" alt="スクリーンショット 2023-11-11 16 41 59" src="https://github.com/Kana-Karin/AWS-CLI-CloudFormation/assets/84316229/7cfee2b9-23ae-4158-a08d-1079224204e7"><br>
   無事、スタックが作成されていることが確認できました。

## Cloudformationでのアーキテクチャ図
![vpc-template](https://github.com/Kana-Karin/AWS-CLI-CloudFormation/assets/84316229/03e47854-41f1-41da-a40b-6f71adf906d8)

## スタックをCLIから作成する上で参照させていただいたサイト
[Qiita - AWS CloudFormation の初歩 備忘録](https://qiita.com/namoshika/items/528d8a50f399b998b14b)<br>
[AWS公式 - 組み込み関数リファレンス](https://docs.aws.amazon.com/ja_jp/AWSCloudFormation/latest/UserGuide/intrinsic-function-reference.html)<br>
[AWS公式 - テンプレートの基礎に関する説明](https://qiita.com/namoshika/items/528d8a50f399b998b14b)<br>

## つまづいた部分、セキュリティベストプラクティスについて
- 今回はベストセキュリティプラクティスに沿ったスタックが作成できなかったこと
- スタックの値の読み込みに時間がかかったこと

