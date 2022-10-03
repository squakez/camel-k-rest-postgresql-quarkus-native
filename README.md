# Camel K CICD Integration

## Namespace preparation

k create namespace development
k create namespace production

## Camel K operator preparation

kamel install -n development
kamel install -n production

## Database preparation

Development environment:

k apply -f db/conf-dev.yaml
k create secret generic my-datasource --from-file datasource-dev.properties -n development

Production environment:

k apply -f db/conf-prod.yaml
k create secret generic my-datasource --from-file datasource-prod.properties -n production

### Populate DB

Development:

kubectl exec -it postgres-dev-xxxxxxxx-yyyyy -n development -- psql -U postgresadmin --password postgresdb
CREATE TABLE customers (name TEXT PRIMARY KEY, city TEXT);

Production:

kubectl exec -it postgres-prod-xxxxxxxx-yyyyy -n production -- psql -U postgresadmin --password postgresdb
CREATE TABLE customers (name TEXT PRIMARY KEY, city TEXT);