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

