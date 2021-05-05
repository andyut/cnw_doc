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

B -..-> C1[[CNW INVENTORY CONSUME]]
E[PLASTIK OUT] -->C


```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTg5NzE3NjM1OCwtMTcwNTY4MDQ5NCwtNz
MyMTc2ODI2LDEyNTMxOTE0MDJdfQ==
-->