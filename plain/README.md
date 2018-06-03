
* tomcatディレクトリ直下の `webapps` フォルダに、warファイルを置くと自動で解凍＆展開してくれる。
  * 自動展開オフの設定も出来るので、その場合は展開されない。また、tomcat起動中にwarファイルが更新されると再度展開される（hotdeploy）
* warファイルは単なるzipファイルなので、 `unzip` コマンドで解凍できる。
* springもtomcatも単なるjarでしかない。javaから起動しているだけのイメージ。


# 動かすまでの手順

```bash

■Java8インストール
sudo apt-get -y install openjdk-8-jdk

■tomcat7落として解凍
wget http://ftp.kddilabs.jp/infosystems/apache/tomcat/tomcat-7/v7.0.88/bin/apache-tomcat-7.0.88.tar.gz
tar -zxvf apache-tomcat-7.0.88.tar.gz
cd apache-tomcat-7.0.88

■JAVA_HOMEを設定
JAVA_HOME=$(readlink -f /usr/bin/javac | sed "s:/bin/javac::")
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
echo $JAVA_HOME

■CATALINA_HOMEとCATALINA_BASEも設定
CATALINA_HOME=$(pwd)
export CATALINA_HOME
echo $CATALINA_HOME

CATALINA_BASE=$CATALINA_HOME
export CATALINA_BASE
echo $CATALINA_BASE

■起動
sh ./bin/catalina.sh start
ps ax | grep tomcat
curl http://localhost:8080/

```
