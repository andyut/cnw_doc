# SAP Pembelian  
## Checklist dan troubleshoot


## Gambaran Umum

Di SAP Business One Pembelian terdiri dari 8 komponen

|SAP Transtype Code | Name |Table Name |
| ------ | ------| ------|
| 22 | Purchase Order|OPOR|
| 20 | Good Receipt PO|OPDN|
| 18 | AP Invoice|OPCH|
| 19 | AP Credit Memo|ORPC|
| 21 | Good Return|ORPD|
| 30 | Jurnal Entry|JDT1|
| 69 | Landed Cost|IPF|

Semua komponen diatas bermuara di 2 table utama SAP, yaitu OINM ( Inventory Audit Report) , dan JDT1 ( Jurnal Entry)

```mermaid
graph LR
A[OPDN] -->|createdby,transtype| x[OINM]
B[OPCH] -->|createdby,transtype| x[OINM]
C[IPF] -->|createdby,transtype| x[OINM]
D[ORPC] -->|createdby,transtype| x[OINM]

A[OPDN] -->|transid| y[JDT1]
B[OPCH] -->|transid| y[JDT1]
C[IPF] -->|transid| y[JDT1]
D[ORPC] -->|transid| y[JDT1]
E[ORPD] -->|transid| y[JDT1]



E[ORPD] -->|createdby,transtype| x[OINM]
```

## Laporan Pembelian 

Dapat Dicek dari 3 bagian modul
* **1. Purchase Analysis**
* **2. Inventory Audit Report**
* **3. General Ledger**
* **4. Laporan HPP Global**


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcyMTIxNTYxMSwtNDA1OTQwNzg4LC0xMD
g1MTUxNjMxLC0xNjkyMDg1NTMzXX0=
-->