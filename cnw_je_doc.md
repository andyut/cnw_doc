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
Penomoran SAP berdasarkan pilihan Type ini 

```python
[bk] = [BK]{year}{month}[999999]
[bd] = [BD]{year}{month}[999999]
[kk] = [KK]{year}{month}[999999]
[kd] = [KD]{year}{month}[999999]
[jv] = [JV]{year}{month}[999999]
[jl] = [JL]{year}{month}[999999]
```

**Is Remark Printed** : Remark di line di print pada voucher di Jurnal Penyesuaian, jika tidak di Thick maka remark nya dicetak  

**Is SAP Partner** : Berhubungan dengan SAP business Partner atau tidak

```mermaid
graph TD
A --> B{Is SAP Partner?}

B -->|No| C(Input Manual Partner atau dikosongkan ==Optional== )
B -->|Yes| D(Pilih list Partner dari drownDown menu)
D -->E{Tidak ada Di List}
E -->|Yes| F(Load / Refresh BP di menu Account-Setting)
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg5NTY0NzI3MiwxMTAwODM4NzY2LC0xMT
YwMDcxNDU5LDE4NTgwNDMxOCwzMDMxODMxMSwtNDEyMjIxNjYx
LDEwNzcxODA0MjAsLTE3MDM5OTU4OTcsLTE5NTUwOTQ4ODIsND
MwNjg5MDExLC0yMDg4NzQ2NjEyXX0=
-->