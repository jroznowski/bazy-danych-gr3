# Lab 08 rozwiązania zadań

## Zadanie 1
* Zadanie 1.1
```sql
CREATE TABLE wyprawa LIKE wikingowie.wyprawa;
INSERT INTO wyprawa SELECT * FROM wikingowie.wyprawa;
CREATE TABLE etapy_wyprawy LIKE wikingowie.etapy_wyprawy;
INSERT INTO etapy_wyprawy SELECT * FROM wikingowie.etapy_wyprawy;
CREATE TABLE sektor LIKE wikingowie.sektor;
INSERT INTO sektor SELECT * FROM wikingowie.sektor;
CREATE TABLE uczestnicy LIKE wikingowie.uczestnicy;
INSERT INTO uczestnicy SELECT * FROM wikingowie.uczestnicy;
```
* Zadanie 1.2
```sql
SELECT k.nazwa FROM kreatura k WHERE k.idKreatury NOT IN (SELECT id_uczestnika FROM uczestnicy);
```
* Zadanie 1.3
```sql
SELECT w.nazwa, SUM(e.ilosc) FROM wyprawa w JOIN uczestnicy u ON u.id_wyprawy = w.id_wyprawy JOIN ekwipunek e ON e.idKreatury = u.id_uczestnika GROUP BY w.nazwa;
```
## Zadanie 2
* Zadanie 2.1
```sql
SELECT w.nazwa, COUNT(u.id_uczestnika), GROUP_CONCAT(k.nazwa) FROM wyprawa w JOIN uczestnicy u ON w.id_wyprawy = u.id_wyprawy JOIN kreatura k ON u.id_uczestnika = k.idKreatury GROUP BY w.nazwa;
```
* Zadanie 2.2
```sql
SELECT w.nazwa AS wyprawa, et.dziennik, s.nazwa AS sektor, k.nazwa AS kierownik FROM etapy_wyprawy et JOIN sektor s ON et.sektor = s.id_sektora JOIN wyprawa w ON et.idWyprawy = w.id_wyprawy JOIN kreatura k ON k.idKreatury = w.kierownik ORDER BY w.data_rozpoczecia ASC, et.idEtapu ASC;
```
## Zadanie 3
* Zadanie 3.1
```sql
SELECT IFNULL(COUNT(et.sektor), 0), s.nazwa FROM etapy_wyprawy et RIGHT JOIN sektor s ON et.sektor = s.id_sektora GROUP BY s.nazwa;
```
* Zadanie 3.2
```sql
SELECT k.nazwa, IF(COUNT(u.id_uczestnika) = 0, 'nie brał udziału w wyprawie', 'brał udział w wyprawie') FROM kreatura k LEFT JOIN uczestnicy u ON k.idKreatury = u.id_uczestnika GROUP BY k.nazwa;
```
## Zadanie 4
* Zadanie 4.1
```sql
SELECT w.nazwa, sum(length(et.dziennik)) FROM etapy_wyprawy et JOIN wyprawa w ON et.idWyprawy = w.id_wyprawy GROUP BY idWyprawy HAVING sum(length(et.dziennik)) < 400;
```
* Zadanie 4.2
```sql
SELECT w.nazwa, ((SUM(z.waga*e.ilosc)/COUNT(DISTINCT u.id_uczestnika))) AS srednia_waga FROM wyprawa w JOIN uczestnicy u ON w.id_wyprawy = u.id_wyprawy JOIN ekwipunek e ON u.id_uczestnika = e.idKreatury JOIN zasob z ON e.idZasobu = z.idZasobu GROUP BY w.nazwa;
```
## Zadanie 5
* Zadanie 5.1
```sql
SELECT k.nazwa,DATEDIFF(w.data_rozpoczecia,k.dataUr) FROM kreatura k JOIN uczestnicy u ON u.id_uczestnika = k.idKreatury JOIN wyprawa w ON w.id_wyprawy = u.id_wyprawy JOIN etapy_wyprawy ew ON u.id_wyprawy = ew.idWyprawy WHERE ew.sektor = '7';
```
