# openldap-clients

A simple Alpine linux container image with openldap-clients installed

Use following commands to build & push to Quay.io
```
docker build --pull -t quay.io/enterprisecoding/openldap-clients:latest .
docker push quay.io/enterprisecoding/openldap-clients:latest
```

Usage:

```
docker run -it --rm quay.io/enterprisecoding/openldap-clients -LLL -x -h "<HOST>" -D "<LDAP_USER>" -w "<PASSWORD>" -b "dc=enterprisecoding,dc=com" "(cn=Fatih Boy)" cn samaccountname userprinciplename mail
```

p.s.: replace HOST, LDAP_USER,PASSWORD with related values