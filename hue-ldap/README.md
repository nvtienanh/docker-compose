
## Sử dụng

Chạy tất cả các container cần thiết:

```
make up
```

Dừng tất cả các contianer đang chạy:

```
make down
```

## Tạo user đăng nhập vào Hue

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

Truy cập thông qua địa chỉ: http://localhost:8888 và sử dụng thông tin account vừa tạo để đang nhập
