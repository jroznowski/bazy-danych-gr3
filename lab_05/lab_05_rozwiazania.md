# Lab 05 rozwiązania zadań

## Zadanie 1
* Zadanie 1 a)
```sql
DELETE from postac WHERE NOT nazwa='Bjorn' AND rodzaj='wiking' ORDER BY wiek DESC LIMIT 2;
```
* Zadanie 1 b)
```sql
ALTER TABLE przetwory DROP FOREIGN KEY przetwory_ibfk_1;
ALTER TABLE przetwory DROP FOREIGN KEY przetwory_ibfk_2;
ALTER TABLE walizka DROP FOREIGN KEY walizka_ibfk_1;
ALTER TABLE postac MODIFY id_postaci int NOT NULL, DROP PRIMARY KEY;
```

## Zadanie 2
* Zadanie 2 a)
```sql
ALTER TABLE postac ADD pesel char(11) first;
UPDATE postac set pesel='17763874635'+id_postaci;
ALTER TABLE postac ADD PRIMARY KEY(pesel);
```
* Zadanie 2 b)
```sql
ALTER TABLE postac MODIFY COLUMN rodzaj enum('wiking','ptak','kobieta','syrena');
```
* Zadanie 2 c)
```sql
INSERT INTO postac (pesel,id_postaci,nazwa,rodzaj,data_ur,wiek) VALUES ('17763874643','8','Gertruda Nieszczera','syrena','1980-03-03', '43');
```

## Zadanie 3
* Zadanie 3 a)
```sql
UPDATE postac SET statek='Bizon' WHERE nazwa LIKE '%a%'
```
* Zadanie 3 b)
```sql
UPDATE statek SET max_ladownosc=0.7*max_ladownosc WHERE data_wodowania BETWEEN '1901-01-01' AND '2000-12-31';
```
* Zadanie 3 c)
```sql
ALTER TABLE postac ADD CHECK (wiek<1000);
```

## Zadanie 4
* Zadanie 4 a)
```sql
ALTER TABLE postac MODIFY rodzaj enum('wiking','ptak','kobieta','syrena','wąż');
INSERT INTO postac (pesel, id_postaci, nazwa, rodzaj, data_ur, wiek) VALUES ('17763874644', '9', 'Loko', 'wąż', '2010-09-09', '13');
```
* Zadanie 4 b)
```sql
CREATE TABLE marynarz LIKE postac;
INSERT INTO marynarz SELECT * FROM postac WHERE statek IS NOT NULL;
```
* Zadanie 4 c)
```sql

```

## Zadanie 5
* Zadanie 5 a)
```sql
UPDATE postac SET statek=NULL;
```
* Zadanie 5 b)
```sql
DELETE FROM postac WHERE nazwa = 'Erik';
```
* Zadanie 5 c)
```sql
DELETE FROM statek;
```
* Zadanie 5 d)
```sql
ALTER TABLE postac DROP FOREIGN KEY postac_ibfk_1;
DROP TABLE statek;
```
* Zadanie 5 e)
```sql
CREATE TABLE zwierz(
id INT AUTO_INCREMENT PRIMARY KEY,
nazwa VARCHAR(40),
wiek INT UNSIGNED);
```
* Zadanie 5 f)
```sql
INSERT INTO zwierz (nazwa, wiek) SELECT nazwa, wiek FROM postac WHERE rodzaj='ptak' OR rodzaj='wąż';
```
