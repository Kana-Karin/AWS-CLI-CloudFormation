# AWS-CLI-CloudFormation
AWS CLIを利用してCloudFormationスタック作成を行います。<br>
今回は無料枠でVPC作成、リソースを使用せず作成していきます。

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
<img width="319" alt="スクリーンショット 2023-11-10 21 18 04" src="https://github.com/Kana-Karin/AWS-CLI-CloudFormation/assets/84316229/5106d922-9ada-44e2-91b0-df02b221d268">

3. **CloudFormationテンプレートの準備、作成**<br>
   今回は、**my-stack**, **mytemplate.yaml**でスタックを作成します。<br>
   ``file://``には.yamlファイルがあるディレクトリを指定します。<br>
   ``aws cloudformation create-stack --stack-name my-stack --template-body file://./aws-cloudformation/mytemplate.yaml``<br>
<img width="４34" alt="スクリーンショット 2023-11-11 16 25 22" src="https://github.com/Kana-Karin/AWS-CLI-CloudFormation/assets/84316229/e107e16b-4611-4767-a2f5-0b217648636c"><br>
スタックがcreateされました。

4. **実際にコンソール画面に行って確認**
