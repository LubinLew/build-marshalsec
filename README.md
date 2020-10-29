# build marshalsec on CentOS7

## install JDK

[Download Java SE Development Kit 15](https://www.oracle.com/java/technologies/javase-jdk15-downloads.html)

## install Maven

### [Download Apache Maven](https://maven.apache.org/download.cgi)

```bash
wget https://apachemirror.sg.wuchna.com/maven/maven-3/3.6.3/binaries/apache-maven-3.6.3-bin.tar.gz
tar xf apache-maven-3.6.3-bin.tar.gz -C /usr/local
mv /usr/local/apache-maven-3.6.3 /usr/local/maven
mkdir -p /usr/local/maven/repo

echo "export "MAVEN_HOME=/usr/local/maven" >> /etc/profile
echo "export "PATH=$PATH:$MAVEN_HOME/bin" >> /etc/profile
source /etc/profile
```

### config Maven

```bash
#  /usr/local/maven/conf/settings.xml

<localRepository>/usr/local/maven/repo</localRepository>


<mirror>
  <id>alimaven</id>
  <name>aliyun-maven-mirror</name>
  <url>http://maven.aliyun.com/nexus/content/groups/public/</url>
  <mirrorOf>central</mirrorOf>
</mirror>
```

## BUILD

```bash
mvn clean package -DskipTests
```