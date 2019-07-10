---
layout: section-page
title:  "DB-Purge"
section: 02,01,01
tags: troubleshoot
---

# Purging Records from PatientWay Databases

Note when purging records ensure that you do not exhaust your transaction log space. Work in smaller amounts by increasing the number of months back to search.

## PW Kiosk

Clearing old working values from Kiosk Encounters. Most encounter values that start with '_' are related to the handling of the kiosk interaction, not the data that is retrieved and revised. Purging these records will  impact our ability to describe 'what happened'. Usually 1 month is acceptable.

```mssql
h
```

Other encounter values can hold less than useful values as well. These queries gives insight into the quantity and the sizes of encounter values. You can use this information to build a list of bulky values that would not be missed.

```mssql
select count(*),name
  from encounter_values
  where name like '[_]%'
  and name != '_encounter_status' 
  and encounter_id < (
    select MAX(id) from encounters 
      where created_at < DATEADD(month, -9, getdate())
    )
    group by name
    order by count(*)

select len(full_value),name
  from encounter_values
  where name like '[_]%'
  and name != '_encounter_status' 
  and encounter_id < (
  select MAX(id) from encounters 
    where created_at < DATEADD(month, -9, getdate())
  )
  -- order by len(full_value) desc
```

## PW Call Queue

Delete Versions table which provides a historical log of what happened to a specific record.

```mssql
delete from versions where item_type in ('CallQueue','Hl7Appt','Hl7Message','Hl7Patient') and created_at < DATEADD(month, -12, getdate())
```

Finding other culprits that may consume version history.

```mssql
select count(*),item_type from versions where created_at>dateadd(month, -2, getdate())  group by item_type;
select count(*),convert(date,created_at) from versions where created_at>dateadd(month, -2, getdate()) group by convert(date,created_at) order by convert(date,created_at)
```

## All Applications

There are several database actions that will free up additional empty space at the database level. Do this only once you are certain you have a good backup.

```mssql
salter database [pw_prod] set recovery simple;
DBCC SHRINKFILE (N'pw_prod' , 0, TRUNCATEONLY);
DBCC SHRINKFILE (N'pw_prod_log' , 0, TRUNCATEONLY);
DBCC SHRINKDATABASE(N'pw_prod' );
alter database [pw_prod] set recovery full;
```
