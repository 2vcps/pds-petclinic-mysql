# How to Demo Petclinc (Cloud) with PDS

## Deploy MySql Service
Deploy a MySQL DataService 

## Gather Info
Get the vip 
Get the user and pw

## Setup the Credentials and Connection String Secret
Place them in `00-secrets.yaml`

## Create Services and Prereqs
`kubectl apply -f prep/`

## Deploy App
`kubectl apply -f deploy/`

`kubectl -n spring-petclinic get svc`
1. paste the api service loadbalancer into your browswer.
2. view and create data.
3. view the metrics in PDS.
4. Do failover/DR demos if you wish.