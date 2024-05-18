# README

## 超絶簡単なVue.js環境構築

### 1. ディレクトリ作成

```sh
mkdir vuejs_test
cd vuejs_test
```

### 2. vue createコマンドでvue-appプロジェクトを作成

```sh
docker run --rm -v ${PWD}:/app -w /app node:14-alpine sh -c "npm install -g @vue/cli && vue create -d vue-app"
```

### 3. vue-appディレクトリへ移動

```sh
cd vue-app
```

### 4. Dockerfile作成

```sh
touch Dockerfile
```

以下のコードをコピペします。

```Dockerfile
# ベースイメージ
FROM node:14-alpine

# 作業ディレクトリの設定
WORKDIR /app

# パッケージファイルをコピー
COPY package*.json ./

# 依存関係のインストール
RUN npm install

# アプリケーションのソースをコピー
COPY . .

# 開発サーバーのポートを公開
EXPOSE 8080

# アプリケーションの起動
CMD ["npm", "run", "serve"]
```

### 5. docker-compose.yml作成

vuejs_testディレクトリに戻ります。

```sh
cd ..
touch docker-compose.yml
```

以下のコードをコピペします。

```yml
version: '3.8'
services:
  vue-app:
    build: ./vue-app
    ports:
      - "8080:8080"
    volumes:
      - ./vue-app:/app
    stdin_open: true
    tty: true
```

### 6. ビルド

```sh
docker-compose build
```

### 7. 環境起動

```sh
docker-compose up
```

<http://localhost:8080>にアクセスすることで、HelloWorld画面が表示されます。


