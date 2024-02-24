# イメージを取得
FROM php:8.3.2-fpm
# 独自のphp.iniファイル(PHPの設定ファイル)を 
# コンテナ内の/usr/local/etc/php/ディレクトリにコピー
COPY php.ini /usr/local/etc/php/

# パッケージやPHPの拡張モジュールをインストールするコマンド　を実行
# PostgreSQLの開発ライブラリをインストール
RUN apt-get update && apt-get install -y \
	git \
	curl \
	zip \
	unzip \
	libpq-dev \ 
    && docker-php-ext-install pdo_pgsql

# vscode ユーザーを作成し、sudo 権限を付与
  RUN useradd -m vscode && \
      echo "vscode:vscode" | chpasswd && \
			usermod -s /bin/bash vscode

# 以降のコマンドを vscode ユーザーとして実行
USER vscode

# 作業ディレクトリを/var/wwwに設定
WORKDIR /var/www