# How to run Webpacker in Docker container

* Build Rails Docker image

```sh
$ docker build -t myrails myrails
```

* Run `rails new`

```sh
$ docker run -it --rm -v $(pwd):/workdir myrails rails new myproject --skip-bundle
$ cd myproject
```

* Add webpacker and mysql2 to Gemfile

```sh
$ echo "gem 'webpacker'" >> Gemfile
$ echo "gem 'mysql2'" >> Gemfile
```

* Run `bundle install`

```sh
$ docker run -it --rm -v $(pwd):/workdir myrails bundle install --path vendor/bundle
```

* Run `rails webpacker:install`

```sh
$ docker run -it --rm -v $(pwd):/workdir myrails rails webpacker:install
```

* Run dev server

```sh
$ cd ..
$ docker-compose up -d
$ docker-compose ps
$ docker-compose logs myproject
```

Visit [http://127.0.0.1:3000](http://127.0.0.1:3000)

* Build your app Docker image

```sh
$ docker build -t myapp myproject
```

* Run your app

```sh
$ docker run -d -p 3000:3000 myapp
```
