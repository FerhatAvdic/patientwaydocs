---
layout: section-page
title:  Search Sch Config
section: 03,02,01
tags: Phs
---

Config file

\PW-AMP\PW_ENV_scripts\pw-config.SITEID.yml

```yaml
phs_connection:
  ALL:
    adapter: "jdbc"
    driver: "net.sourceforge.jtds.jdbc.Driver"
    username: "sql_server_user"
    password: "sql_server_password"
    adtsys_id: "8"
    hnumasgnauth_id:
      ca_ns: 1
      ca_nb: 3
      ca_nl: 4
      ca_pe: 5
      ca_qc: 6
      ca_on: 7
      ca_mb: 8
      ca_sk: 9
      ca_ab: 10
      ca_bc: 11
      ca_yt: 12
      ca_nu: 13
      ca_nt: 14
    recurring_patient_type_codes:
      - "31"
      - "35"
      - "310"
      - "103"
  PROD:
    url: "jdbc:jtds:sqlserver://SQL_SERVER_HOST/PHSDB;tds=8.0;lastupdatecount=true"
    password: "AtB92!zw%"
  STAGE:
    url: "jdbc:jtds:sqlserver://ch-psmsqlprod/phsprod;tds=8.0;lastupdatecount=true"
    password: "AtB92!zw%"
  UAT:
    url: "jdbc:jtds:sqlserver://142.239.152.170/phstrain;tds=8.0;lastupdatecount=true"
     #url: "jdbc:jtds:sqlserver://142.239.212.233/phstrain;tds=8.0;lastupdatecount=true"
  DEV:
    url: "jdbc:jtds:sqlserver://142.239.152.170/phstest;tds=8.0;lastupdatecount=true"
    # url: "jdbc:jtds:sqlserver://142.239.212.233/phstrain;tds=8.0;lastupdatecount=true"
```