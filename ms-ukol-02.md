# Matematická statistika - Úkol č. 2
Pro tento úkol jsem použil seed `212` (neboť mé datum narození je 2. 12.).
```r
set.seed(212);
n <- sample(200:300, size=1);
indexy <- sample(1:1851, size=n);
data <- STAR[indexy,];
```
## 1. Úkol
### Zadání
Dosahují děti z malých tříd lepších studijních výsledků než děti z klasické třídy? Porovnání proveďte zvlášť pro matematiku a zvlášť pro čtení.
### Řešení
Nejprve si naše data rozdělíme na 2 části:
```r
data_mensi_trida <- subset(data, Class == 'small')
data_klasicka_trida <- subset(data, Class == 'regular')
```

## 2. Úkol
### Zadání

## 3. Úkol
### Zadání

## 4. Úkol

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwMTA5NjA2NDYsLTE4NjMxNzU1MzksLT
E0MjQ1MTkyMDZdfQ==
-->