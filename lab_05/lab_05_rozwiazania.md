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
INSERT INTO postac (pesel,id_postaci,nazwa,rodzaj,data_ur) VALUES ('17763874643','8','Gertruda Nieszczera','syrena','1980-03-03', '43')
```
