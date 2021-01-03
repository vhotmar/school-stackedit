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
```
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
Poté se také můžem podívat na histogramy těchto 2 datasetuů pro výsledky jak z matematiky, tak ze čtení:
```r
make_histogram <- function(data, x, title, subtitle) {
  ggplot(data, aes(x = eval(parse(text = x)), fill = Class)) +
    geom_histogram(bins = 10, size = .2, colour='black') +
    labs(title = title, subtitle = subtitle, y = "Počet", x = "Skóre") +
    theme(legend.position = "none")
}

p1 <- make_histogram(data_mensi_trida, "Math", "Výsledky z matematiky", "Menší třída") + xlim(400, 600)
p2 <- make_histogram(data_klasicka_trida, "Math", "Výsledky z matematiky", "Klasická třída") + xlim(400, 600)
p3 <- make_histogram(data_mensi_trida, "Read", "Výsledky ze čtení", "Menší třída") + xlim(350, 550)
p4 <- make_histogram(data_klasicka_trida, "Read", "Výsledky ze čtení", "Klasická třída") + xlim(350, 550)

(p1 + p3) / (p2 + p4)
```
Výsledkem tohoto kódu jsou následující grafy:
![Graf](https://raw.githubusercontent.com/vhotmar/school-stackedit/main/ms_plot_01_01.svg)
Vidíme, že 
## 2. Úkol
### Zadání

## 3. Úkol
### Zadání

## 4. Úkol

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA0NTE1MDA0MSw2NTM5NzgyMzYsODA2Nz
kwOTM2LC0xODYzMTc1NTM5LC0xNDI0NTE5MjA2XX0=
-->