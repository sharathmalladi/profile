## Installing Hadoop (version 2.7.3) on ubuntu

Source Link: https://www.codementor.io/java/tutorial/how-to-setup-hadoop-in-pseudo-distributed-mode-on-single-cluster

### Create folders for java and hadoop
##### ($HADOOP_HOME points to /home/hadoop/hadoop-2.7.3)

sudo mkdir /home/hadoop
sudo mkdir -p /usr/local/java
sudo mkdir -p /hadoop_store/hdfs /hadoop_store/hdfs/namenode /hadoop_store/hdfs/datanode
sudo mkdir -p ${HADOOP_HOME}/tmp
sudo mkdir -p ${HADOOP_HOME}/logs

### Setup java

wget --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u112-b15/jre-8u112-linux-x64.tar.gz  
wget --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u112-b15/jdk-8u112-linux-x64.tar.gz  
sudo cp -r jre-*.tar.gz /usr/local/java  
sudo cp -r jd*.tar.gz /usr/local/java  
cd /usr/local/java  
sudo tar xvzf jdk-8u112-linux-x64.tar.gz  
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/local/java/jre1.8.0_112/bin/java" 1  
sudo update-alternatives --install "/usr/bin/javac" "javac" "/usr/local/java/jdk1.8.0_112/bin/javac" 1  
sudo update-alternatives --install "/usr/bin/javaws" "javaws" "/usr/local/java/jre1.8.0_112/bin/javaws" 1  
sudo update-alternatives --set java /usr/local/java/jre1.8.0_112/bin/java  
sudo update-alternatives --set javac /usr/local/java/jdk1.8.0_112/bin/javac  
sudo update-alternatives --set javaws /usr/local/java/jre1.8.0_112/bin/javaws  
java -version  
sudo apt-get install ssh  
sudo apt-get install rsync  

### Setup hadoop
wget http://www-eu.apache.org/dist/hadoop/common/hadoop-2.7.3/hadoop-2.7.3.tar.gz  
sudo cp -r hadoop-2.7.3.tar.gz /home/hadoop/  
cd /home/hadoop  
sudo tar xvzf hadoop-2.7.3.tar.gz  

### Setup hadoop group and hduser user accounts
addgroup hadoop  
sudo adduser --ingroup hadoop hduser  

### Grant permissions to hduser
sudo chown -R hadoop /home/hadoop  
sudo chown -R hadoop /hadoop_store  
sudo adduser hduser sudo  

### Edit hadoop configuration files (core-site.xml, hdfs-site.xml, etc)

### Manually edit hadoop-env.sh and fix this line: export JAVA_HOME=/usr/local/java/jdk1.8.0_112

### start hadoop daemons
start-datanode  
start-namenode  
start-node-manager  
start-resource-manager  

