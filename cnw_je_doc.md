# CNW JE
## Petunjuk Penggunaan

###### Author : Andy   
###### Project : CNW Project  
###### Generated Using : *Markdown*
  
---
[toc]
---
## Keterangan  

CNW JE modul yang digunakan untuk memasukan **Jurnal Entry SAP** menggunakan ***web Services Intidata***.  Mencakup Jurnal entry, cost center, control account, cetakan vocher.

### Menu 
```mermaid
graph TD
A(CNW JE) --> B(List Voucher)
A(CNW JE) --> C(Income / Expense)
A(CNW JE) --> D(SAP Jurnal Entry)
A(CNW JE) --> E(Account Setting)
```

### Sub Menu

```mermaid
graph LR
A(List Voucher) --> A1(Voucher / Kasbon)
B(Income / Expense) --> B1(Entertain)
C(SAP Jurnal Entry) --> C1(Journal Entry)
D(Account Setting) --> D1(Account)
D(Account Setting) --> D2(Department)
D(Account Setting) --> D3(Divisi)
D(Account Setting) --> D4(Expense Type)
D(Account Setting) --> D5(SAP Business Partner)


```
### Modul Integrated
Semua modul tambahan yang berkaitan dengan *biaya*, akan integrated ke ***CNW-JE***, contoh biaya pengiriman, 
```mermaid
graph BT
A(*CNW-Expense) --> B(CNW-JE)
A1(*CNW-Entertain) --> B(CNW-JE)
A2(*CNW-Voucher) --> B(CNW-JE)
A3(*CNW-Shipment) --> B(CNW-JE)
A4(*CNW-DebitNote) --> B(CNW-JE)
A5(*CNW-SKI) --> B(CNW-JE)
A6(*CNW-Surveyor) --> B(CNW-JE)
```
	-Integrasi masih dalam pengembangan- 
---  
## List Voucher -> Voucher

Form 

	Catatan : Belum Integrated dengan Jurnal Entry SAP

## Income / Expense -> Entertain
Form
	Catatan : Belum Integrated dengan Jurnal Entry SAP


## SAP Jurnal Entry -> Jurnal Entry

### Form View
![Odoo](https://www.dropbox.com/s/w8tgqavs7sjxsmu/WhatsApp%20Image%202021-04-27%20at%205.29.23%20PM.jpeg?dl=1)

Mapping dengan SAP Business One

![SAP B1](https://www.dropbox.com/s/md3aqf9uwd0sn2d/WhatsApp%20Image%202021-04-27%20at%205.29.24%20PM.jpeg?dl=1)



### Field 
**Name** : Nomor Internal Jurnal Entry CNW
**Company** : Company yang aktif
**Doc Date** : Tanggal dokumen
**Type** : Jenis Jurnal Entry
	Daftar Jenis Tipe Jurnal Entry :
* JL : Jurnal Lain
* JV : Jurnal Penyesuaian
* BK : Bank Kredit
* BD : Bank Debet
* KK : Kas Kredit
* KD : Kas Debet

	Jika pilihan BK, BD, KD, KK maka cetakannya akan muncul jenis cetakan *Voucher pengeluaran/penerimaan kas/bank*. Jika pilihannya JV,JL maka cetakannya akan muncul cetakan *Jurnal Penyesuaian / Pemindahan*

```mermaid
graph TD
A[JE] --> B{Type?}
B -->|BK, BD,KK,KD| C[Kasbon Penerimaan / Pengeluaran]
B -->|JV,JL| D[Jurnal Penyesuaian / Pemindahan]

```

Penomoran SAP berdasarkan pilihan Type ini 

```python
[bk] = [BK]{year}{month}[999999]
[bd] = [BD]{year}{month}[999999]
[kk] = [KK]{year}{month}[999999]
[kd] = [KD]{year}{month}[999999]
[jv] = [JV]{year}{month}[999999]
[jl] = [JL]{year}{month}[999999]
```

**Is Remark Printed** : Remark di line di print pada voucher di Jurnal Penyesuaian, jika tidak di ==Thick==  maka remark nya dicetak  

**Is SAP Partner** : Berhubungan dengan SAP business Partner atau tidak

```mermaid
graph TD
A --> B{Is SAP Partner?}

B -->|No| C(Input Manual Partner atau dikosongkan ==Optional== )
B -->|Yes| D(Pilih list Partner dari drownDown menu)
D -->E{Tidak ada Di List}
E -->|Yes| F(Load / Refresh BP di menu Account-Setting)
```
Catatan : Untuk COA Tipe **Control Account** ,  Check List ini harus posisi **Yes**, karena kode BP tersebut akan masuk ke dalam ***CardCode*** Didalam Table Jurnal entry (  *JDT1* )

**Partner SAP** : Dropdown untuk memilih SAP Partner, jika tipe Account menggunakan **Control Account**  maka akan masuk ke dalam CardCode di JDT1 , dan Business Card ID di UDF JDT1.  Jika Tidak menggunakan **Control Account** maka akan ditempel nama customer di field remarks

**Other Partner** : Partner diluar SAP business One Partner.








<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ0Nzk1NDEyOCwtMTU0OTM5MTIyMSwtMT
c4MzM4NjI3NSwtMjA0ODIzMzE0MSwtMTQ4Mjg1MDAwOCwtNjg4
MjUxMjEyLC04OTU2NDcyNzIsMTEwMDgzODc2NiwtMTE2MDA3MT
Q1OSwxODU4MDQzMTgsMzAzMTgzMTEsLTQxMjIyMTY2MSwxMDc3
MTgwNDIwLC0xNzAzOTk1ODk3LC0xOTU1MDk0ODgyLDQzMDY4OT
AxMSwtMjA4ODc0NjYxMl19
-->