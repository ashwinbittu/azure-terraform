---
title: Delegate DNS Domain to Azure DNS 
description: Learn to Delegate DNS Domain to Azure DNS 
---
## Important Note: DNS Domain
- This demo requires registered DNS Domain, if you don't have one just please go through the demo to know more about Azure Public DNS Zones

## Step-01: Introduction
- Understand about
  - Domain Registrar
  - DNS Zones


## Step-02: DNS Zones - Create DNS Zone
- Go to Service -> **DNS Zones**
- **Subscription:** 
- **Resource Group:** dns-zones
- **Name:** kubeoncloud.com
- **Resource Group Location:** East US
- Click on **Review + Create**

## Step-03: Make a note of Azure Nameservers
- Go to Services -> **DNS Zones** -> **kubeoncloud.com**
- Make a note of Nameservers
```
ns1-04.azure-dns.com.
ns2-04.azure-dns.net.
ns3-04.azure-dns.org.
ns4-04.azure-dns.info.
```

## Step-04: Update Nameservers at your Domain provider (Mine is AWS)
- **Verify before updation**
```
nslookup -type=SOA kubeoncloud.com
nslookup -type=NS kubeoncloud.com
```
- Go to AWS Route53 (This is my Domain Provider)
- Go to Services -> Route53 -> Registered Domains -> kubeoncloud.com
- Click on **Add or edit name servers**
- Update Azure Name servers here and click on **Update**
- Click on **Hosted Zones**
- Delete the hosted zone with name **kubeoncloud.com**
- **Verify after updation**
```
nslookup -type=SOA kubeoncloud.com 8.8.8.8
nslookup -type=NS kubeoncloud.com 8.8.8.8
```
