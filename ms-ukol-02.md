# Matematická statistika - Úkol č. 2
Pro tento úkol jsem použil seed `212` (neboť mé datum narození je 2. 12.). Dále načteme potřebné knihovny pro pohodlnou práci s R.
```r
library(ggplot2)
library

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
Poté se podíváme na to jak tyto data vypadají:
```r
> summary(data_mensi_trida)
      Math            Read                     Class      Sex        Race    Lunch   
 Min.   :405.7   Min.   :393.9   regular          : 0   boy :33   black:26   no :39  
 1st Qu.:454.3   1st Qu.:415.9   regular.with.aide: 0   girl:35   other: 0   yes:29  
 Median :481.2   Median :430.4   small            :68             white:42           
 Mean   :482.5   Mean   :434.2                                                       
 3rd Qu.:513.1   3rd Qu.:450.2                                                       
 Max.   :576.9   Max.   :538.2                                                       
> summary(data_klasicka_trida)
      Math            Read                     Class      Sex        Race    Lunch   
 Min.   :392.8   Min.   :378.6   regular          :88   boy :45   black:26   no :48  
 1st Qu.:458.1   1st Qu.:421.1   regular.with.aide: 0   girl:43   other: 0   yes:40  
 Median :484.8   Median :431.2   small            : 0             white:62           
 Mean   :490.4   Mean   :435.0                                                       
 3rd Qu.:520.5   3rd Qu.:448.7                                                       
 Max.   :603.0   Max.   :518.0       
```

![Graf](https://raw.githubusercontent.com/vhotmar/school-stackedit/main/ms_plot_01_01.svg)
## 2. Úkol
### Zadání

## 3. Úkol
### Zadání

## 4. Úkol

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NjE3MjA4MDksNjUzOTc4MjM2LDgwNj
c5MDkzNiwtMTg2MzE3NTUzOSwtMTQyNDUxOTIwNl19
-->