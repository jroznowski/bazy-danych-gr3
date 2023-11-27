# Lab 06 rozwiązania zadań

## Zadanie 1
* Zadanie 1.1
```sql
CREATE TABLE kreatura SELECT * FROM wikingowie.kreatura;
CREATE TABLE zasob SELECT * FROM wikingowie.zasob;
CREATE TABLE ekwipunek SELECT * FROM wikingowie.ekwipunek;
```
* Zadanie 1.2
```sql
SELECT * from zasob;
```
* Zadanie 1.3
```sql
SELECT * from zasob WHERE rodzaj='jedzenie';
```
* Zadanie 1.4
```sql
SELECT idZasobu,ilosc, idKreatury from ekwipunek WHERE idKreatury IN (1,3,5);
```
## Zadanie 2
* Zadanie 2.1
```sql
SELECT * FROM kreatura WHERE rodzaj != 'wiedzma' AND udzwig >= 50;
```
* Zadanie 2.2
```sql
SELECT * FROM zasob WHERE waga BETWEEN 2 AND 5;
```
* Zadanie 2.3
```sql
SELECT * FROM kreatura WHERE nazwa LIKE '%or%' AND udzwig BETWEEN 30 AND 70;
```
## Zadanie 3
* Zadanie 3.1
```sql
SELECT * FROM zasob WHERE MONTH(dataPozyskania) = 07 OR MONTH(dataPozyskania) = 08;
```
* Zadanie 3.2
```sql
SELECT * FROM zasob WHERE rodzaj IS NOT NULL ORDER BY waga;
```
* Zadanie 3.3
```sql
SELECT * FROM kreatura WHERE dataUr IS NOT NULL ORDER BY dataUr LIMIT 5;
```
## Zadanie 4
* Zadanie 4.1
```sql
SELECT DISTINCT rodzaj FROM zasob;
```
* Zadanie 4.2
```sql
SELECT CONCAT(nazwa, ' - ', rodzaj) FROM kreatura WHERE rodzaj LIKE 'wi%';
```
* Zadanie 4.3
```sql
SELECT *, CONCAT(ilosc*waga) FROM zasob WHERE YEAR(dataPozyskania) BETWEEN 2000 AND 2007;
```
## Zadanie 5
* Zadanie 5.1
```sql
SELECT 0.7*waga AS NETTO, 0.3*waga AS ODPADKI FROM zasob;
```
* Zadanie 5.2
```sql
SELECT * FROM zasob WHERE rodzaj IS NULL;
```
* Zadanie 5.3
```sql
SELECT DISTINCT rodzaj FROM zasob WHERE nazwa LIKE 'Ba%' OR nazwa LIKE '%os' ORDER BY rodzaj;
```
