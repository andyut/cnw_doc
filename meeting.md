# Pembelian Plastik

## Skema 1
### Masuk dalam stock SAP
```mermaid
graph TD
A[ PLASTIK IN] --> B(PO / AP INVOICE)
B --> C[[STOCK CARD]]

D(PLASTIK OUT) --> E(GOOD ISSUE)
E -->C


```


## Skema 2
###  Biaya di SAP, stock card diluar SAP
```mermaid
graph TD
A[ PLASTIK IN] --> B(CNW EXPENSE)
B --> C[[SAP JURNAL ENTRY]]

D(PLASTIK OUT) --> E(GOOD ISSUE)
E -->C


```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MTYyNjMxMDcsLTE3MDU2ODA0OTQsLT
czMjE3NjgyNiwxMjUzMTkxNDAyXX0=
-->