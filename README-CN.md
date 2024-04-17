# 文档

## Nacos

```bash
docker run -d --name nacos -e MODE=standalone -p 8848:8848 -d nacos/nacos-server:2.0.2
```

## Deploy

```bash
mkdir build
mkdir build/bin build/config build/lib build/logs build/module
```

```bash
cp datalink-doc/bin/auto.sh build/bin
cp datalink-config/src/main/resources/application.properties build/config
cp datalink-config/src/main/resources/application-dev.properties build/config
cp datalink-config/src/main/resources/bootstrap.properties build/config
```

```bash
cp ./datalink-gateway/target/datalink-gateway.jar build/module
cp ./datalink-uaa/target/datalink-uaa.jar build/module
cp ./datalink-dbase/datalink-user/target/datalink-user.jar build/module
cp ./datalink-dlink/datalink-task/target/datalink-task.jar build/module
```

```bash
find . -name "*.jar" -exec cp "{}" build/lib \;
```

```bash
$ cd build/bin
```

```bash
./auto.sh start base

# or

./auto.sh start all

# or

./auto.sh start gateway
```

### frontend

```bash
cd datalink-web

npm i

npm i --save-dev @umijs/plugin-openapi

npm i -g cross-env umi

npm run dev
```