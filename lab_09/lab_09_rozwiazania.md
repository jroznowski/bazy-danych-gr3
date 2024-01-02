# Lab 09 rozwiązania zadań

## Zadanie 1
* Zadanie 1.1
```sql
DELIMITER //
CREATE TRIGGER kreatura_before
BEFORE INSERT ON kreatura
FOR EACH ROW
BEGIN 
  IF NEW.waga <= 0
  THEN
    SET NEW.waga = 1;
  END IF;
END
//
