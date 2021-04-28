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

Menu --> Purchase Analysis  

![Purchase Analysis](https://www.dropbox.com/s/hpcspadwpnxcavv/PURCHASE%20DATA.png?dl=1)


Catatan :
Laporan *Purchase Analysis* SAP Business total tidak termasuk **Freight**, dan **Landed Cost**

Laporan Pembelian SAP berdasarkan AP invoice Dan good Receipt PO. Jika terjadi perbedaan antara GR dan AP , maka akan timbul jurnal HPP di AP invoice

```mermaid
graph TD
A(Good Receipt PO) --> A1(AP Invoice)
A --> A2(Landed Cost) 
A2 -->A3{Stock Ada?}
A3 -->|Y| A4(Bebankan Ke Stock)
A3 -->|N| A5(Bebankan Ke HPP Price Difference)
A3 -->|Kurang| A6(Bebankan Sebagian Ke HPP Price Difference dan stock)
 
A1 --> B{Over missing Qty ?}
B -->|Y| C(Rubah nilai sesuai invoice Supplier)
C --> D{Stock Habis}
D-->|Y| E([selisih dibuang ke HPP Price Difference])
D-->|N| F([dibebankan ke barang yang ada])
F--> H[[ Update ke JDT1 ]]
E -->H[[ Update ke JDT1 ]] 
F--> G[[ Update ke OINM ]]
F--> I[[ Update ke OITW - itemcost ]]


```



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMTk2MzI4OTQsLTU5MTU3OTI4MywtMT
U4NTY0MjQ0NSw0NzQ5OTQ2NjQsLTI1Nzc3MDk0OCwxMjE3ODkx
MjMsMjA5MzY2OTgxOSwtNzIxMjE1NjExLC00MDU5NDA3ODgsLT
EwODUxNTE2MzEsLTE2OTIwODU1MzNdfQ==
-->