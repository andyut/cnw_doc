# SAP Pembelian  
## Checklist dan troubleshoot


## Gambaran Umum

Di SAP Business One Pembelian terdiri dari 8 komponen

|SAP Transtype Code | Name |Table Name |
| ------ | ------| ------|
| 22 | Purchase Order|OPOR|
| 20 | Good Receipt PO|OPDN|
| 204 | AP Down Payment|OPOR|
| 18 | AP Invoice|OPCH|
| 19 | AP Credit Memo|OPOR|
| 21 | Good Return|ORPD|
| 30 | Jurnal Entry|JDT1|
| 69 | Landed Cost|IPR|

Semua komponen diatas bermuara di 2 table utama SAP, yaitu OINM ( Inventory Audit Report) , dan JDT1 ( Jurnal Entry)

```mermaid
graph TD

```

## Laporan Pembelian 

Dapat Dicek dari 3 bagian modul
* **1. Purchase Analysis**
* **2. Inventory Audit Report**
* **3. General Ledger**
* **4. Laporan HPP Global**


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MDgzMTcwNDcsLTEwODUxNTE2MzEsLT
E2OTIwODU1MzNdfQ==
-->