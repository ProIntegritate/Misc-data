Extract specific EventID:
```
wevtutil qe "Microsoft-Windows-Sysmon/Operational" /e:root /q:"*[System [(EventID=1)]]" /F:text
```

Extract specific time period:
```
wevtutil qe "Microsoft-Windows-Sysmon/Operational" /e:root /q:"*[System [TimeCreated[@SystemTime>='2022-07-10T01:00:00' and @SystemTime<'2022-07-10T01:05:00']] ]" /F:text
```

Combining both:
```
wevtutil qe "Microsoft-Windows-Sysmon/Operational" /e:root /q:"*[System [TimeCreated[@SystemTime>='2022-07-10T01:00:00' and @SystemTime<'2022-07-10T02:00:00']]] and *[System [(EventID=1)]]" /F:text
```

Note, there are 3 date fields, don't get these confused:

```
"Date: 2022-07-10T03:59:21.2140000Z" <- Eventlog local time, says ZULU time at the end but really isn't. Missing +2h indicator.
```
```
"UtcTime: 2022-07-10 01:59:21.212"  <- Sysmon time, this is REALLY Zulu/UTC time.
```
```
<TimeCreated SystemTime='2022-07-10T01:59:21.2123412Z'/>	<- This is what XPATH locks on to: [TimeCreated].
```
