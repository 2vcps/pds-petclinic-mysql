# How to Demo Petclinic (Cloud) with PDS

## Deploy MySql Service
Deploy a MySQL Data Service
1. Login to PDS https://prod.pds.portworx.com
2. Click 'MySQL' Under Deploy Data Service
3. Enter mysql ds name.
4. Select Target cluster and Namespace
5. Change Resource and number of nodes if needed.
6. Click Deploy.

## Gather Info
Once MySQL is up.
Get the vip dns entry.
1. On the data service click connection
2. Copy the DNS name for example `my-jowings-k9tqde-mysql-0-vip.sales-staging.pds-dns.io` it should have VIP in the name.
3. Paste this into `01-secrets.yaml` for all three microservices.
4. Now in the PDS UI click the "Copy Password" link.
5. Paste this into `01-secrets.yaml`

## Create Services and Prereqs
`kubectl apply -f prep/`
This will setup the services and secret for Petclinic to connect to MySQL.

## Deploy App
`kubectl apply -f deploy/`

`kubectl -n spring-petclinic get svc`
1. paste the api service loadbalancer into your browswer. For example `a93d12935c58946aeb3a23ad695809e7-2072184173.us-west-2.elb.amazonaws.com` **NOTE** This is an external LB and exposed to the internets. DO NOT Leave this up for too long as unathenticated apps like Petclinic are a perfect target of bad guys.
2. view and create data.
3. view the metrics in PDS.
4. Do PX ENTERPRISE failover/DR demos if you wish.