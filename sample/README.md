
公式サンプルを使って、シンプルなサーブレットを起動してみる

[公式サンプル](https://tomcat.apache.org/tomcat-7.0-doc/appdev/sample/)

# 動かすまでの手順

```bash

■compile（servlet-api.jarのクラスをimportしているため、classpathが必要）
javac -classpath $CATALINA_HOME/lib/servlet-api.jar Hello.java

■war化
cd sample/
jar cf ../sample.war .
mv ../sample.war $CATALINA_HOME/webapps

■起動
# sh $CATALINA_HOME/bin/catalina.sh stop
sh $CATALINA_HOME/bin/catalina.sh start
ps ax | grep tomcat
curl http://localhost:8080/sample

```
