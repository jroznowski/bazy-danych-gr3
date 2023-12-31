# Lab 07 rozwiązania zadań

## Zadanie 1
* Zadanie 1.1
```sql
SELECT AVG(waga) FROM kreatura WHERE rodzaj='wiking';
```
* Zadanie 1.2
```sql
SELECT AVG(waga), COUNT(rodzaj), rodzaj FROM kreatura GROUP BY rodzaj;
```
* Zadanie 1.3
```sql
SELECT AVG(2023-YEAR(dataUr)), rodzaj FROM kreatura GROUP BY rodzaj;
```
## Zadanie 2
* Zadanie 2.1
```sql
SELECT SUM(waga),rodzaj FROM zasob GROUP BY rodzaj;
```
* Zadanie 2.2
```sql
SELECT nazwa, AVG(waga) FROM zasob WHERE ilosc >= 4 GROUP BY nazwa having SUM(waga) > 10;
```
* Zadanie 2.3
```sql
SELECT COUNT(DISTINCT nazwa), rodzaj FROM zasob GROUP BY rodzaj HAVING MIN(ilosc) > 1;
```
## Zadanie 3
* Zadanie 3.1
```sql
SELECT kreatura.nazwa, SUM(ilosc) FROM kreatura JOIN ekwipunek ON ekwipunek.idKreatury = kreatura.idKreatury GROUP BY kreatura.nazwa;
```
* Zadanie 3.2
```sql
SELECT k.nazwa, z.nazwa FROM kreatura k INNER JOIN ekwipunek e ON e.idKreatury = k.idKreatury LEFT JOIN zasob z ON z.idZasobu = e.IdZasobu;
```
* Zadanie 3.3
```sql
SELECT k.nazwa, e.idZasobu FROM kreatura k LEFT JOIN ekwipunek e ON k.idKreatury = e.idKreatury WHERE e.idZasobu IS NULL;
```
## Zadanie 4
* Zadanie 4.1
```sql
SELECT k.nazwa, z.nazwa, k.dataUr FROM kreatura k NATURAL JOIN ekwipunek e LEFT JOIN zasob z ON e.idZasobu = z.idZasobu WHERE k.rodzaj = 'wiking' AND k.dataUr BETWEEN '1670-01-01' AND '1979-12-31'; 
```
* Zadanie 4.2
```sql
SELECT k.nazwa, k.dataUr, z.nazwa FROM kreatura k NATURAL JOIN ekwipunek e LEFT JOIN zasob z ON e.idZasobu = z.idZasobu WHERE z.rodzaj = 'jedzenie' ORDER BY YEAR(k.dataUr) ASC LIMIT 5;
```
* Zadanie 4.3
```sql
SELECT CONCAT(k.nazwa, ' - ', l.nazwa) FROM kreatura k, kreatura l WHERE l.idKreatury - k.idKreatury = 5
```
## Zadanie 5
* Zadanie 5.1
```sql
SELECT AVG(z.waga*e.ilosc), k.rodzaj FROM kreatura k JOIN ekwipunek e ON k.idKreatury = e.idKreatury JOIN zasob z ON e.idZasobu = z.idZasobu WHERE k.rodzaj NOT IN ('małpa','wąż' ) AND e.ilosc < 30 GROUP BY k.rodzaj;
```
* Zadanie 5.2
```sql
SELECT 'najmlodsza', a.maxData, b.nazwa, a.rodzaj FROM (SELECT max(dataUr) maxData, rodzaj FROM kreatura GROUP BY rodzaj) a, (SELECT nazwa, dataUr FROM kreatura) b WHERE a.maxData = b.dataUr
UNION
SELECT 'najstarsza', a.minData, b.nazwa, a.rodzaj FROM (SELECT min(dataUr) minData, rodzaj FROM kreatura GROUP BY rodzaj) a, (SELECT nazwa, dataUr FROM kreatura) b WHERE a.minData = b.dataUr;
```
