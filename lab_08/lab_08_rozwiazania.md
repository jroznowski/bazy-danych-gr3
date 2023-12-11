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
