# Giới thiệu

Docker-compose là một công cụ tuyệt vời để định nghĩa và chạy nhiều container trên ứng dụng Docker. Nó cho phép bạn tạo 1 file cấu hình YAML, nơi mà bạn sẽ định nghĩa các services trên ứng dụng của bạn và định nghĩa tất cả các bước, các cấu hình cần thiết để xây dựng các image, up các container và liên kết chúng với nhau. Cuối cùng, một khi tất cả điều này được thực hiện, bạn sẽ chỉ cần thiết lập tất cả với một lệnh duy nhất.

## Sử dụng

Để Run các container, chạy lệnh:
```
  make up
```

Nếu bạn start thành công thì terminal sẽ hiện ra có dạng:

```bash
$ make up
mkdir -p data
docker network create hadoop-net
be8211c3229a3d811d0b5f85d3184d2349bc58558f698ab8c0957cd10b0a18d5
docker-compose up -d
Creating namenode        ... done
Creating datanode        ... done
Creating historyserver   ... done
Creating nodemanager     ... done
Creating resourcemanager ... done
```

Truy cập vào các ứng dụng của Hadoop:

* Namenode: http://localhost:9870/dfshealth.html#tab-overview
* History server: http://localhost:8188/applicationhistory
* Datanode: http://localhost:9864/
* Nodemanager: http://localhost:8042/node
* Resource manager: http://localhost:8088/

Để Stop các container, chạy lệnh:
```
  make down
```
Khi đó terminal sẽ trả về:
```bash
$ make down
docker-compose down
Stopping datanode        ... done
Stopping namenode        ... done
Stopping historyserver   ... done
Stopping resourcemanager ... done
Stopping nodemanager     ... done
Removing datanode        ... done
Removing namenode        ... done
Removing historyserver   ... done
Removing resourcemanager ... done
Removing nodemanager     ... done
Network hadoop-net is external, skipping
docker network rm hadoop-net
hadoop-net
rm -rf data
```

## Cấu hình Environment

The configuration parameters can be specified in the hadoop.env file or as environmental variables for specific services (e.g. namenode, datanode etc.):
```
  CORE_CONF_fs_defaultFS=hdfs://namenode:9000
```

CORE_CONF corresponds to core-site.xml. fs_defaultFS=hdfs://namenode:9000 will be transformed into:
```
  <property><name>fs.defaultFS</name><value>hdfs://namenode:9000</value></property>
```
To define dash inside a configuration parameter, use triple underscore, such as YARN_CONF_yarn_log___aggregation___enable=true (yarn-site.xml):
```
  <property><name>yarn.log-aggregation-enable</name><value>true</value></property>
```

The available configurations are:
* /etc/hadoop/core-site.xml CORE_CONF
* /etc/hadoop/hdfs-site.xml HDFS_CONF
* /etc/hadoop/yarn-site.xml YARN_CONF
* /etc/hadoop/httpfs-site.xml HTTPFS_CONF
* /etc/hadoop/kms-site.xml KMS_CONF
* /etc/hadoop/mapred-site.xml  MAPRED_CONF

If you need to extend some other configuration file, refer to base/entrypoint.sh bash script.

## Liên hệ
* Anh Nguyen [@nvtienanh](https://github.com/nvtienanh) 

## Tham khảo
* [Big Data Europe](https://github.com/big-data-europe/)
