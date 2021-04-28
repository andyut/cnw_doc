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
**(26) Name** : Nomor Internal Jurnal Entry CNW
**Company** : Company yang aktif
**Doc Date** : Tanggal dokumen
**(2) Type** : Jenis Jurnal Entry
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

**(3) Is Remark Printed** : Remark di line di print pada voucher di Jurnal Penyesuaian, jika tidak di ==Thick==  maka remark nya dicetak  

**(4) Is SAP Partner** : Berhubungan dengan SAP business Partner atau tidak

```mermaid
graph TD
A --> B{Is SAP Partner?}

B -->|No| C(Input Manual Partner atau dikosongkan ==Optional== )
B -->|Yes| D(Pilih list Partner dari drownDown menu)
D -->E{Tidak ada Di List}
E -->|Yes| F(Load / Refresh BP di menu Account-Setting)
```
Catatan : Untuk COA Tipe **Control Account** ,  Check List ini harus posisi **Yes**, karena kode BP tersebut akan masuk ke dalam ***CardCode*** Didalam Table Jurnal entry (  *JDT1* )

**(5) Partner SAP** : Dropdown untuk memilih SAP Partner, jika tipe Account menggunakan **Control Account**  maka akan masuk ke dalam CardCode di JDT1 , dan Business Card ID di UDF JDT1.  Jika Tidak menggunakan **Control Account** maka akan ditempel nama customer di field remarks

**(5) Other Partner** : Partner diluar SAP business One Partner.  
**(6) Tunai/Cheque No** : Kolum untuk memasukan Nomor Cheque .  
**(7) Invoice Ref / Notes** : Nomor Invoice Referensi
**(1) Remark 1** : Kolom keterangan ==(Wajib Diisi)==.  
**(1) Remark 2** : Kolom keterangan tambahan (baris 2).  
**(1) Remark 3** : Kolom keterangan tambahan (baris 3) .  
**(8) Remark 4** : Kolom keterangan Dalam bentuk HTML .  
**(10) Amount** :  Total nilai dari baris yang di *thick* "Printed as Total in Kasbon"
**(11) transID** :  Nomor ID JE SAP Business One  
**(12) Number in SAP** : Kode ==Number==  JE Header SAP Business One  
**(13) U_Trans_No** : Nomor Transaksi Akuntansi SAP Business One  
**(14) Debit, Credit, Balance** : Nilai dibaris Jurnal Entry, Balance **harus = 0**  
**(15) Account** :Account dari SAP Business One    
**(16) Remark** : Keterangan baris   
**(17) Printed as Total In Kasbon** : Jika checklist, maka akan dihitung nilai dari *absolut (Debet - Credit)* , dan terbilangnya. nilai ini yang akan muncul di cetakan kasbon ( khusus untuk BK , BD, KK , KD)    
**(18) Debit** : Nilai debet   
**(19) Credit** : Nilai credit   
**(14) Debit, Credit, Balance** : Nilai dibaris Jurnal Entry, Balance **harus = 0**  
**(14) Debit, Credit, Balance** : Nilai dibaris Jurnal Entry, Balance **harus = 0**  














<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA2NzEyOTM5NiwxNTAxNTgxOTQzLDE0MT
A0ODUwNzMsMjExNDUwMzUxMCwtMTU0OTM5MTIyMSwtMTc4MzM4
NjI3NSwtMjA0ODIzMzE0MSwtMTQ4Mjg1MDAwOCwtNjg4MjUxMj
EyLC04OTU2NDcyNzIsMTEwMDgzODc2NiwtMTE2MDA3MTQ1OSwx
ODU4MDQzMTgsMzAzMTgzMTEsLTQxMjIyMTY2MSwxMDc3MTgwND
IwLC0xNzAzOTk1ODk3LC0xOTU1MDk0ODgyLDQzMDY4OTAxMSwt
MjA4ODc0NjYxMl19
-->