# Matematická statistika - Úkol č. 2
Pro tento úkol jsem použil seed `212` (neboť mé datum narození je 2. 12.).
```r
set.seed(212);
n <- sample(200:300, size=1);
indexy <- sample(1:1851, size=n);
data <- STAR[indexy,];
```
## 1. 
### Zadání
Dosahují děti z malých tříd lepších studijních výsledků než děti z klasické třídy? Porovnání proveďte zvlášť pro matematiku a zvlášť pro čtení.
### Řešení

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MjQ1MTkyMDZdfQ==
-->