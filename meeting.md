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
B --> C[[SAP JURNAL ENTRY BIAYA]]

B -..-> C1[[CNW INVENTORY CONSUME]]
E[PLASTIK OUT] --> E1(CNW STOCK CONSUME)
E1 --> C1

```
<!--stackedit_data:
eyJoaXN0b3J5IjpbNzUwODA0ODYyLC0xNzA1NjgwNDk0LC03Mz
IxNzY4MjYsMTI1MzE5MTQwMl19
-->