## 1、install

    mvn clean package -DskipTests

The tgz installation package apache-inlong-dataproxy-0.9.0-incubating-SNAPSHOT-bin.tar.gz can be found under the inlong-dataproxy/dataproxy-dist/target

un tar it

    tar -zxvf apache-inlong-dataproxy-0.9.0-incubating-SNAPSHOT-bin.tar.gz


## 2、configuration

	cd apache-inlong-proxy-0.9.0-incubating-SNAPSHOT-bin

### config tube

	ip:port are tube address

sed -i 's/TUBE_LIST/ip1:port,ip2:port/g' conf/flume.conf

    change proxy port
    agent1.sources.tcp-source.port = 46801

notice that conf/flume.conf FLUME_HOME is proxy the directory for proxy inner data



### Environmental preparation
	cd bin
	sh prepare_env.sh
	cd ..

### config manager
	vim conf/common.properties
	write：
	cluster_id=1   // cluter id is for future use please write 1
	manager_hosts=ip:port // manager open api 

## 3、run
	sh bin/start.sh

## 4、check
	telnet 127.0.0.1 46801

