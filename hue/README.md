
## Example to use LDAP authentication with Hue

LDAP webui url: https://localhost:6443

Default credentials:

 * User: cn=admin,dc=example,dc=org
 * Password: admin

Example user:

```
dn: uid=hadoopService,dc=example,dc=org
cn: ServiceAccount
ou: People
displayname: Test Bela
givenname: Firstname
mail: hadoopService@example.org
objectclass: top
objectclass: person
objectclass: organizationalPerson
objectclass: inetOrgPerson
sn: Lastname
uid: hadoopService
userpassword: 12345
```


Example group:

```
dn: cn=hue,dc=example,dc=org
objectClass: top
objectClass: groupOfNames
cn: hue
member: uid=hadoopService,dc=example,dc=org
```
