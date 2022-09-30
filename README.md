# camel-k-rest-postgresql-quarkus-native

## Populate DB

kubectl exec -it postgres-dev-ddddc75cb-gxzff -n development -- psql -U postgresadmin --password postgresdb

CREATE TABLE customers (name TEXT PRIMARY KEY, city TEXT);