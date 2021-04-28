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
graph BT
A[OPDN] ---->|createdby| x[OINM]
B[OPCH] ---->|createdby| x[OINM]
C[IPF] ---->|createdby| x[OINM]
D[ORPC] ---->|createdby| x[OINM]
E[ORPD] ---->|createdby| x[OINM]

A[OPDN] -..->|transid| y[JDT1]
B[OPCH] -..->|transid| y[JDT1]
C[IPF] -..->|transid| y[JDT1]
D[ORPC] -..->|transid| y[JDT1]
E[ORPD] -..->|transid| y[JDT1]

```

## Laporan Pembelian 

Dapat Dicek dari 4 bagian modul
* **1. Purchase Analysis SAP**
* **2. Inventory Audit Report**
* **3. General Ledger**
* **4. Laporan HPP Global**


**Purchase Analysis**

Menu --> Purchase Analysis Item
![Purchase Analysis](https://www.dropbox.com/s/tznp53s7e1n1p5i/PURCHASE%20DATA%20ITEM.png?dl=1)


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI5ODExNDU1Myw0NzQ5OTQ2NjQsLTI1Nz
c3MDk0OCwxMjE3ODkxMjMsMjA5MzY2OTgxOSwtNzIxMjE1NjEx
LC00MDU5NDA3ODgsLTEwODUxNTE2MzEsLTE2OTIwODU1MzNdfQ
==
-->