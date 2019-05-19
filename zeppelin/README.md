
## Sử dụng

Chạy tất cả các container cần thiết:

```bash
make up
```
Nếu chạy thành công thì trên terminal sẽ trả về output:

```bash
docker network create spark-net
9386f8b306cd221ddb3b111301d621d17245b9410ba0bc3e56476be733d1e762
docker-compose up -d
Creating phpldapadmin ... done
Creating namenode     ... done
Creating openldap     ... done
Creating hue          ... done
Creating datanode     ... done
Creating spark-master ... done
Creating zeppelin     ... done
Creating spark-worker ... done
```

Dừng tất cả các contianer đang chạy:

```
make down
```
Khi đó terminal sẽ trả về:

```bash
docker-compose down
Stopping spark-worker ... done
Stopping zeppelin     ... done
Stopping spark-master ... done
Stopping datanode     ... done
Stopping hue          ... done
Stopping namenode     ... done
Stopping openldap     ... done
Stopping phpldapadmin ... done
Removing spark-worker ... done
Removing zeppelin     ... done
Removing spark-master ... done
Removing datanode     ... done
Removing hue          ... done
Removing namenode     ... done
Removing openldap     ... done
Removing phpldapadmin ... done
Network spark-net is external, skipping
docker network rm spark-net
spark-net
```

## Tạo user đăng nhập vào LDAP Admin

Truy cập vào LDAP Admin webui url: https://localhost:6443

Đăng nhập vào với thông tin addmin user:

 * User: cn=admin,dc=example,dc=org
 * Password: admin

Sau khi đã năng nhập, tạo user Hue:

```
dn: uid=nvtienanh,dc=example,dc=org
cn: ServiceAccount
ou: People
displayname: Test Bela
givenname: Firstname
mail: nvtienanh@example.org
objectclass: top
objectclass: person
objectclass: organizationalPerson
objectclass: inetOrgPerson
sn: Lastname
uid: nvtienanh
userpassword: 12345
```

Tạo group:

```
dn: cn=hue,dc=example,dc=org
objectClass: top
objectClass: groupOfNames
cn: hue
member: uid=nvtienanh,dc=example,dc=org
```

## Đăng nhập vào Hue

Truy cập vào địa chỉ http://localhost:8888 với thông tin tài khoản đã được tạo bằng LDAP Admin


## Đăng nhập vào Zeppelin

http://localhost:8080 với thông tin tài khoản đã được tạo bằng LDAP Admin


