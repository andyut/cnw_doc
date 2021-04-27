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
---  
## List Voucher -> Voucher

Form 

	Catatan : Belum Integrated dengan Jurnal Entry SAP

## Income / Expense -> Entertain
Form
	Catatan : Belum Integrated dengan Jurnal Entry SAP


## SAP Jurnal Entry -> Jurnal Entry

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
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzAzMTgzMTEsLTQxMjIyMTY2MSwxMDc3MT
gwNDIwLC0xNzAzOTk1ODk3LC0xOTU1MDk0ODgyLDQzMDY4OTAx
MSwtMjA4ODc0NjYxMl19
-->