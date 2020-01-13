# hasura-prisma-test

This is a demo repo to reproduce the following issue:https://github.com/hasura/graphql-engine/issues/3695

To reproduce:
```bash
git clone https://github.com/Tbaut/hasura-prisma-test.git
cd hasura-prisma-test
docker-compose up
# ^ this needs to be done twice sometimes... ¯\_(ツ)_/¯
```
Hasura console will be on http://localhost:8888

Then apply the migration
```
cd hasura-migration
hasura-dev migrate apply
```

From the console try to add a remote relationship :
![image](https://user-images.githubusercontent.com/33178835/72279213-f03e4200-3635-11ea-83e7-33de950b7794.png)

Adding a remote relationship fails with:
```
"path": "$.args[0].args",
"error": "ExpectedTypeButGot (TypeNamed (Nullability {unNullability = True}) (NamedType {unNamedType = Name {unName = "ID"}})) (TypeNamed (Nullability {unNullability = True}) (NamedType {unNamedType = Name {unName = "Int"}})) :| []",
"code": "remote-schema-error"
```
