# Matematická statistika - Úkol č. 2
Pro tento úkol jsem použil seed `212` (neboť mé datum narození je 2. 12.). Dále načteme potřebné knihovny pro pohodlnou práci s R.
```r
library(ggplot2)
library(patchwork)

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
Poté se také můžem podívat na histogramy těchto 2 datasetuů pro výsledky jak z matematiky, tak ze čtení:
```r
make_histogram <- function(data, x, title, subtitle) {
  ggplot(data, aes(x = eval(parse(text = x)), fill = Class)) +
    geom_histogram(bins = 10, size = .2, colour='black') +
    geom_vline(aes(xintercept = mean(eval(parse(text = x)))), color = "black", linetype = "dashed", size=1) +
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

![Graf](https://raw.githubusercontent.com/vhotmar/school-stackedit/main/ms_plot_01_01.svg?t=2)

Z grafů můžeme odhadnout že distribuce výsledků z matematiky i ze čtení bude pro obě dvě třídy velice podobná (svislá čára ukazuje průměr).

Ze zadání máme ověřit, zda děti z malých tříd dosahují lepších výsledků než děti z klasických tříd. Označme si $X_i$ - výsledky studentů z menší třídy a $Y_i$ - výsledky studentů z klasické třídy. To, že je jedna třída dosahuje lepších výsledků můžeme ověřit podle toho zda střední hodnota $X_i$ je větší než střední hodnota $Y_i$. Jelikož nic bližšího o distribucích $X_i$ a $Y_i$ nevím, náš **model** bude $\mathcal{F}=\lbrace F_X \in \mathcal{L}^2_+, F_Y \in \mathcal{L}^2_+ \rbrace$. **Testované parametry**, jsou $\mu_{X}=\mathbb{E}X$ a $\mu_{Y}=\mathbb{E}Y$ a naše **nulová hypotéza** bude:
$$H_0: \mu_{X}-\mu_{Y}=0$$
Tedy že mezi střední hodnotou obou nezávislých výběrů není rozdíl a naše **alternativa** bude:
$$H_1: \mu_{X}>\mu_{Y}$$
Tedy, že střední hodnota $X_i$ je vyšší než střední hodnota $Y_i$. Z těchto informací je zřejmé že můžeme využít *dvouvýběrový t-test bez předpokladu shody rozptylu*. **Testovanou statistikou** tedy je:
$$\widetilde{T}_{n,m}=\frac{\overline{X}_n-\overline{Y}_m}{\sqrt{S^2_X/n+S^2_Y/m}}$$
**Kritickým oborem** je:

## 2. Úkol
### Zadání
Je pravdivé tvrzení, že více než polovina dětí má nárok na oběd zdarma?
### Řešení
```r
> summary(data$Lunch)
 no yes 
125 115 
```

## 3. Úkol
### Zadání

## 4. Úkol

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk5NDAyNDU0NSwxNjI1ODc4OTEwLC03MD
czMTMyMDgsNjUzOTc4MjM2LDgwNjc5MDkzNiwtMTg2MzE3NTUz
OSwtMTQyNDUxOTIwNl19
-->