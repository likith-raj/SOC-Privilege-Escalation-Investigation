\# Splunk Detection Queries



\## Failed Login



```spl

index=\* EventCode=4625

```



\## Successful Login



```spl

index=\* EventCode=4624

```



\## New User Created



```spl

index=\* EventCode=4720

```



\## User Added to Administrators



```spl

index=\* EventCode=4732

```



\## Combined Detection



```spl

index=\* (EventCode=4625 OR EventCode=4624 OR EventCode=4720 OR EventCode=4732)

| eval Activity=case(

EventCode=4625,"Failed Login",

EventCode=4624,"Successful Login",

EventCode=4720,"New User Created",

EventCode=4732,"Added to Administrators"

)

| table \_time EventCode Activity host

| sort \_time

```

