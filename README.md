# AWS-CLI-CloudFormation
AWS CLIを利用してCloudFormationスタック作成を行います。

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
出力フォーマットにはjson,text,tableが選択できます。S3やDBを使用する際、可読性が高いのはtableフォーマットらしいので、今回はtableを指定します。<br>
``cat ~/.aws/credentials``を利用して確認します。<br>
<img width="619" alt="スクリーンショット 2023-11-10 21 18 04" src="https://github.com/Kana-Karin/AWS-CLI-CloudFormation/assets/84316229/5106d922-9ada-44e2-91b0-df02b221d268">

3. **CloudFormationテンプレートの準備**
