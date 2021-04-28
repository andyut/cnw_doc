# **CNW TRC**

## *Panduan Penggunaan*  

	Author : Dika , Andy
	Version : 1.1

----

[toc]  


----

## Keterangan

Modul TRC merupakan tracking dan prepare dokumen untuk menyiapkan barang di gudang. terdiri dari 3 bagian utama
1. Get Data dari SAP Business One
2. Check List Sales Admin untuk dikirim ke gudang
3. Checklist Gudang untuk penerimaan SO, dan prepare untuk barang
4. Print Out tally dan Picking berdasarkan Jalur.


## Alur Dokumen

```mermaid
graph TD
A(Sales Order) --> A1([Sales Order Confirmed])
A1 -->A2{Posting To SAP Success?}
A2 -->|N| A3([Cek Blocking / Credit Limit, etc])
A2 -->|Y| A4([Cek Blocking / Credit Limit, etc])


```


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4MDczNzY0NzIsMTYyNDkyODcxMSwtMT
U4OTM1MzU3Myw5NzEyNzg2NzFdfQ==
-->