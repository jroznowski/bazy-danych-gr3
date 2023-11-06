# Lab 04 rozwiązania zadań

## Zadanie 1
* Zadanie 1.1
```sql
CREATE TABLE postac (
id_postaci int NOT NULL AUTO_INCREMENT,
nazwa varchar(40),
rodzaj enum('wiking','ptak','kobieta'),
data_ur date,
wiek int unsigned,
PRIMARY KEY ('id_postaci')
);
```
* Zadanie 1.2
```sql
INSERT INTO postac VALUES
(default,'Bjorn','wiking','1984-01-01',39),
(default,'Drozd','ptak','2023-08-08',1),
(default,'Tesciowa','kobieta','1959-01-01',64);
```
* Zadanie 1.3
```sql
UPDATE postac SET wiek=88 WHERE nazwa='Tesciowa';
```
## Zadanie 2
* Zadanie 2.1
```sql
CREATE TABLE walizka (
id_walizki INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
pojemnosc INT UNSIGNED,
kolor enum('rozowy','czerwony','teczowy','zolty'),
id_wlasciciela INT NOT NULL,
FOREIGN KEY (id_wlasciciela) REFERENCES postac(id_postaci) ON DELETE CASCADE
);
```
* Zadanie 2.2
```sql
ALTER TABLE walizka ALTER kolor SET DEFAULT 'rozowy';
```
* Zadanie 2.3
```sql
INSERT INTO walizka VALUES
(default,10,'czerwony',1),
(default,7,default,3);
```

## Zadanie 3
* Zadanie 3.1
```sql
CREATE TABLE izba (
adres_budynku VARCHAR(40) NOT NULL, 
nazwa_izby VARCHAR(40) NOT NULL,
metraz INT UNSIGNED,
wlasciciel INT,
PRIMARY KEY (adres_budynku, nazwa_izby),
FOREIGN KEY (wlasciciel) REFERENCES postac(id_postaci) ON DELETE SET NULL
);
```
* Zadanie 3.2
```sql
ALTER TABLE izba ADD kolor_izby VARCHAR(40) DEFAULT 'czarny' AFTER metraz;
```
* Zadanie 3.3
```sql
INSERT INTO izba VALUES ('Bukowa 1', 'spizarnia', 15, default, 1);
```

## Zadanie 4
* Zadanie 4.1
```sql
CREATE TABLE przetwory (
id_przetworu INT NOT NULL AUTO_INCREMENT PRIMARY KEY,
rok_produkcji INT(4) DEFAULT '1654',
id_wykonawcy INT,
zawartosc VARCHAR(40),
dodatek VARCHAR(40) DEFAULT 'papryczka chilli',
id_konsumenta INT,
FOREIGN KEY (id_wykonawcy) REFERENCES postac(id_postaci),
FOREIGN KEY (id_konsumenta) REFERENCES postac(id_postaci)
);
```

* Zadanie 4.2
```sql
INSERT INTO przetwory VALUES (default, 1999, 1, 'bigos', default, 3);
```

## Zadanie 5
* Zadanie 5.1
```sql
INSERT INTO postac (nazwa, rodzaj, data_ur, wiek) VALUES 
('Frode', 'wiking', '1983-02-02', 40), 
('Halfdan', 'wiking', '1982-03-03', 41), 
('Erik', 'wiking', '1981-04-04', 42),
('Gorm', 'wiking', '1980-05-05', 43),
('Birger', 'wiking', '1979-06-06', 44);
```

* Zadanie 5.2
```sql
CREATE TABLE statek (
nazwa_statku VARCHAR(40) NOT NULL PRIMARY KEY,
rodzaj_statku enum('byrding', 'knara', 'sneka'),
data_wodowania DATE,
max_ladownosc INT UNSIGNED
);
```

* Zadanie 5.3
```sql
INSERT INTO statek VALUES 
('Bizon', 'sneka', '2020-06-06', 50),
('Czarny Kruk', 'byrding', '2021-05-05', 30);
```

* Zadanie 5.4
  * a)
  ```sql
  ALTER TABLE postac ADD funkcja VARCHAR(40);
  ```
* Zadanie 5.5
```sql
UPDATE postac SET funkcja='kapitan' WHERE nazwa='Bjorn';
```

* Zadanie 5.6
```sql
ALTER TABLE postac ADD statek VARCHAR(40), ADD FOREIGN KEY(statek) REFERENCES statek(nazwa_statku);
```

* Zadanie 5.7
```sql
UPDATE postac SET statek='Bizon' WHERE rodzaj='wiking' OR rodzaj='ptak';
```

* Zadanie 5.8
```sql
DELETE FROM izba WHERE nazwa_izby='spizarnia';
```

* Zadanie 5.9
```sql
DROP TABLE izba;
```

