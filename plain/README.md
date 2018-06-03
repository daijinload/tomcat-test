
* tomcatディレクトリ直下の `webapps` フォルダに、warファイルを置くと自動で解凍＆展開してくれる。
  * 自動展開オフの設定も出来るので、その場合は展開されない。
  * また、tomcat起動中にwarファイルが更新されると再度展開される（hotdeploy）
* warファイルは単なるzipファイルなので、 `unzip` コマンドで解凍できる。
* springもtomcatも単なるjarでしかない。javaから起動しているだけのイメージ。


# 動かすまでの手順

```bash

■Java8インストール
sudo apt-get -y install openjdk-8-jdk

■tomcat7落として解凍
cd ~/src
wget http://ftp.kddilabs.jp/infosystems/apache/tomcat/tomcat-7/v7.0.88/bin/apache-tomcat-7.0.88.tar.gz
tar -zxvf apache-tomcat-7.0.88.tar.gz

■環境変数を.bashrcに設定
cat << EOS >> .bashrc

### Java(open-jdk) Tomcat
JAVA_HOME=$(readlink -f /usr/bin/javac | sed "s:/bin/javac::")
export JAVA_HOME
PATH=$PATH:$JAVA_HOME/bin
export PATH
echo $JAVA_HOME

CATALINA_HOME=~/src/apache-tomcat-7.0.88
export CATALINA_HOME
echo $CATALINA_HOME

CATALINA_BASE=$CATALINA_HOME
export CATALINA_BASE
echo $CATALINA_BASE

EOS

■起動
sh $CATALINA_HOME/bin/catalina.sh start
ps ax | grep tomcat
curl http://localhost:8080/

```
