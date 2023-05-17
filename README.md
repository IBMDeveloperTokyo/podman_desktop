# podman_desktop

## イメージのPULL
まずはコンテナの元となるイメージをPULLします。
左側にあります、メニューバーから **Images** をクリックします。（図①）
Images画面表示後、画面上部にあります **Pull an image** をクリックします。（図②）
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/2603b98a-da76-6396-3e0f-022b75e9a984.png)

**Image to Pull** にPULLしたいイメージを入力します。（図①）
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/850f94a6-b23c-7079-420b-d47ee46530e5.png)

今回はサンプルにありました、`redhat/ubi8-micro`を入力します。
その後、下部にあります **Pull image** をクリックします。（図①）
![image.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/b0e214ce-4436-d712-df8d-51c9c74a727e.png)

イメージのPULLが開始されると **Pull image** 下部に実行状況が出力されます。
PULLが完了すると **Pull image** から **Done** に変わるので、 **Done** をクリックします。（図①）
![pull_image_004.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/d046aef0-3c06-d988-1b7b-ec8b820c208b.png)

Images画面に戻ると、イメージがPULLされたことを確認できます。（図①）
![pull_image_005.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/c7dfcc9c-07cd-2ca0-2c9b-3548b6a109ef.png)

CLIで同様の処理を行う場合は下記のコマンドを実行する必要があります。
```
podman pull redhat/ubi8-micro
```

## イメージの削除
イメージを削除する方法は以下の3つとなります。
1. 個別削除
1. 選択削除
1. 全削除（※未実行イメージのみ）

### 1. 個別削除
イメージの右側にある **ゴミ箱アイコン** をクリックすると、該当イメージを削除できます。（図①）
![rmi_001.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/682a30e6-e289-bb2b-a480-19b8f0ecb5db.png)

CLIで同様の処理を行う場合は下記のコマンドを実行する必要があります。
```
podman rmi docker.io/redhat/ubi8-micro
```

### 2. 選択削除
削除したいイメージの左側にある **チェックボックスにチェック** をし（図①）、検索テキストボックス右側に表示される **ゴミ箱アイコン** をクリックすると、選択したイメージを削除できます。（図①）
![rmi_002.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/3491f601-8581-87cd-f4b3-6ab8a02cf918.png)

CLIで同様の処理を行う場合は下記のコマンドを実行する必要があります。
```
podman rmi registry.access.redhat.com/ubi7 docker.io/library/my-custom-image
```

### 3. 全削除（※未実行イメージのみ）
Images画面右上部にある **Prune images** をクリックします。（図①）
![rmi_003.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/12b4cb81-2899-da5d-b4ae-b337623baef6.png)

CLIで同様の処理を行う場合は下記のコマンドを実行する必要があります。
```
podman rmi -a
```

確認メッセージが表示されるので **Yes** をクリックすると、全ての未実行イメージを削除できます。（図①）
![rmi_004.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/bae62254-0f79-ccb4-0a74-c13cb609bff0.png)

## イメージのビルド
イメージはPULLするだけでなく、Containerfile（Dockerfile）を使用してビルドすることもできます。

Images画面右上部にある **Build an image** をクリックします。（図①）
![build_001.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/bdd668df-5286-9230-4c83-52a4768b47f1.png)

**Containerfile path**をクリックするとファイル選択画面が表示されるので、ビルド対象のContainerfileを選択します。（図①）
![build_002.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/0881712a-38c9-4161-fef2-d859ebcfbee2.png)

Containerfileを選択すると、 **Build context directory** にContainerfileのパスが自動でセットされます。
変更したい場合は **Build context directory**をクリックするとディレクトリ選択画面が表示されるので、ビルドコンテキストディレクトリを選択します。（図①）
**Image Name**には新しいイメージ名を入力します。（図②）
各種入力後、 **Build** をクリックすると、ビルドが開始されます。（図③）
![build_003.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/efb2ac3c-0628-f702-17f0-c2bd5bc255ea.png)

ビルドが開始されると実行状況が出力されます。
ビルドが完了すると **Done** が表示されるので、 **Done** をクリックします。（図①）
![build_004.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/dbdffe11-54a0-b610-8bc0-d3741231535b.png)

Images画面に戻ると、イメージがビルドされたことを確認できます。（図①）
![build_005.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/e41ef192-23c1-4d53-d98b-9b1f430714e2.png)

CLIで同様の処理を行う場合は下記のコマンドを実行する必要があります。
```
podman build -t my-custom-image -f C:\Dojo\20230526\Dockerfile C:\Dojo\20230526
```

## コンテナRUN
イメージを使ってコンテナを起動します。

コンテナ起動したいイメージの右側にある **再生アイコン** をクリックします。（図①）
![run_001.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/f4569e6b-789d-da73-0cac-ef419fef0fe8.png)

コンテナ起動に必要な構成情報を設定します。

**Container name** にコンテナ名を入力します。（図①）
![run_002.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/b2193fdd-436b-b8b0-a86a-045e22391cee.png)

コンテナからホストPCのディレクトリにアクセスできるようにしたい場合、 **Volumes** の **Path on the host** にホストPCのディレクトリ（図①）を、 **Path inside the container**にコンテナのディレクトリを入力します（図②）
**Path on the host** については右側にある **ディレクトリアイコン** をクリックすると、ディレクトリ選択画面が表示され、GUIによるディレクトリの選択が可能です。
追加で設定を行いたい場合、右側にある **+アイコン** をクリックすると追加設定用の入力欄が表示されます。（図③）
![run_003.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/9e3d620d-70f6-5593-d872-2df74ec369c7.png)

**Port mapping** には設定が必要なポートが表示されるので、該当するホストPCのポート番号を入力します。（図①）
追加でポートの設定を行いたい場合、 **Add custom port mapping** をクリックすると追加設定用の入力欄が表示されます。（図②）
![run_004.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/f0b80f5a-7944-ec26-d8f2-a991008a8ed7.png)

環境変数を設定する場合は**Environment variables** の **Name** に環境変数名（図①）、 **Value** に値を入力します。（図②）
![run_005.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/05aec6e9-ef35-137c-54ec-b4fcdcca9efe.png)

必要に応じて、その他のタブの設定も行います。

構成情報の設定が完了したら、 **Start Container** をクリックします。（図①）
![run_006.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/2e94eb18-0459-9974-4d2b-6cae3d7514c6.png)

Containers画面が表示され、時間経過とともにコンテナが起動されたことを確認できます。（図①）
![run_007.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/88806004-f00f-9836-a7ae-3264544d5374.png)

コンテナ名をクリックして、コンテナの詳細を確認してみます。
**Inspectタブ** をクリックすると、該当コンテナのyamlを確認することができます。
![run_008.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/b059bf60-1372-6817-0cf9-298930bb96c5.png)

35行目等で **Container name** （図①）、45行目等で **Volumes** （図②）の入力内容を確認することができます。
![run_009.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/4b4f8a15-bd1a-6aa0-2c1d-8fe5190c4719.png)

53～72行目等で **Port mapping** の入力内容を確認することができます。（図①）
![run_010.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/08997df0-026a-4a6f-7610-6008bb5c020e.png)

195行目等で **Environment variables** の入力内容を確認することができます。（図①）
![run_011.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/714d97a9-1da6-81c6-7fcc-441c17ba501e.png)

Webブラウザからもコンテナが起動されたことを確認してみます。
http://localhost:8080 を開くと"JBoss EAP 6"のTOPページが表示されます。
![run_012.png](https://qiita-image-store.s3.ap-northeast-1.amazonaws.com/0/2715466/764b784e-dc07-10d6-627b-7ad4d62f6b67.png)


CLIで同様の処理を行う場合は下記のコマンドを実行する必要があります。
```
podman run -d --name dojo20230526 -v C:\Dojo\20230526:/usr/dojo20230526 -p 8080:8080 -p 9990:9990 -p 9999:9999 -e ENV_NAME=test docker.io/library/my-custom-image:latest
```

## イメージのタグつけ

## イメージPUSH
