- rails-for-webpackerイメージをビルドする

```sh
docker build -t rails-for-webpacker rails-for-webpacker
```

- rails newする

```sh
docker run -it --rm -v $(pwd):/workdir rails-for-webpacker rails new project --skip-bundle
cd project
```

- Gemfileにwebpackerを追加する

- bundle installする

```sh
docker run -it --rm -v $(pwd):/workdir rails-for-webpacker bin/bundle install --path vendor/bundle
```

- webpacker installする

```sh
docker run -it --rm -v $(pwd):/workdir rails-for-webpacker bin/rails webpacker:install
```

- webpacker install vueする

```sh
docker run -it --rm -v $(pwd):/workdir rails-for-webpacker bin/rails webpacker:install:vue
```

- サーバー起動する

```sh
cd ..
docker-compose up -d
docker-compose ps
docker-compose logs project
```

- 起動したら`http://127.0.0.1:3000`

- 成果物をビルドする

```sh
docker build -t project project
```

- 成果物を起動する

```sh
docker run -d -p 3000:3000 project
```
