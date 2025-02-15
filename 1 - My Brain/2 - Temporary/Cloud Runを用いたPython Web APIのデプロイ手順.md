---
created: 2025-02-15
tags: 
description: 
reference: https://youtu.be/02TrOBYrJkU?si=K2NqWBkn9qWotV5n
---
**1. ローカル環境での準備**

- Flaskアプリケーションの作成
    - Cloud Runを使用する際は、ポート番号を環境変数 `PORT` から取得するように設定する必要があります。
- Dockerfileの作成
    - `Dockerfile`ファイルを作成し、Dockerイメージのビルド手順を記述します。
    - Pythonのベースイメージを使用し、必要なパッケージをインストールします。
    - アプリケーションコードをイメージにコピーし、実行権限を付与します。
    - `PORT` 8080でアプリケーションを起動するように設定します。
- Dockerイメージのビルド
    - `docker build`コマンドを使用して、Dockerイメージをビルドします。
    - `-t`オプションでイメージにタグを付けます。
- ローカル環境での動作確認
    - `docker run`コマンドを使用して、Dockerコンテナを起動します。
    - `-p`オプションでポートフォワーディングを設定し、ローカルマシンからアクセスできるようにします。
    - WebブラウザでAPIのエンドポイントにアクセスし、動作を確認します。

**2. Cloud Runへのデプロイ**

- Google Cloudプロジェクトの作成
    - Google Cloud Platformのコンソールで、新しいプロジェクトを作成します。
- Cloud Run APIの有効化
    - プロジェクトでCloud Run APIを有効にします。
- Cloud SDKのインストールと認証
    - ローカルマシンにCloud SDKをインストールします。
    - `gcloud init`コマンドを実行し、Cloud SDKを認証します。
- Cloud Runへのデプロイ
    - `gcloud run deploy`コマンドを使用して、DockerイメージをCloud Runにデプロイします。
    - `--source`オプションでDockerイメージのパスを指定します。
    - `--platform-managed`オプションを指定します。
    - `--allow-unauthenticated`オプションを指定し、認証なしでAPIにアクセスできるようにします。
- デプロイの確認
    - デプロイが完了したら、Cloud RunのコンソールでサービスのURLを確認します。
    - WebブラウザでサービスのURLにアクセスし、APIが動作することを確認します。

**参考資料**

- Cloud Runのドキュメント: [https://cloud.google.com/run/docs](https://cloud.google.com/run/docs)
- Flaskのドキュメント: [https://flask.palletsprojects.com/en/latest/](https://flask.palletsprojects.com/en/latest/)
- Dockerのドキュメント: [https://docs.docker.com/](https://docs.docker.com/)
- k6のドキュメント: [https://k6.io/docs/](https://k6.io/docs/)