# MySQL Functions Tutorial

Questa repository prova ad offrire una guida base sui comandi di MySQL

## Indice
1. [Funzioni](#funzioni)
    - [Creazione di un Database](#creazione-di-un-database)
    - [Selezione di un Database](#selezione-di-un-database)
    - [Inserimento di Dati](#inserimento-di-dati)
    - [Selezione di Dati](#selezione-di-dati)
    - [Aggiornamento di Dati](#aggiornamento-di-dati)
    - [Eliminazione di Dati](#eliminazione-di-dati)
    - [Eliminazione di una Tabella](#eliminazione-di-una-tabella)
    - [Eliminazione di un Database](#eliminazione-di-un-database)
    - [Filtrare i Risultati](#filtrare-i-risultati)
    - [Ordinare i Risultati](#ordinare-i-risultati)
    - [Contare i Record](#contare-i-record)
    - [Calcolare la Media](#calcolare-la-media)
    - [Utilizzo di NOT IN](#utilizzo-di-not-in)
    - [Condizioni con AND e OR](#condizioni-con-and-e-or)
    - [Utilizzo di LEFT JOIN](#utilizzo-di-left-join)
      
---

# Funzioni

## Creazione di un Database

Per creare un database MySQL si utilizza il comando:

```sql
CREATE DATABASE nome_database;
```

Esempio:

```sql
CREATE DATABASE negozio;
```

Questo comando crea un nuovo database chiamato `negozio`.

## Selezione di un Database

Dopo aver creato un database, per utilizzarlo bisogna selezionarlo con:

```sql
USE nome_database;
```

Esempio:

```sql
USE negozio;
```

Ora tutte le operazioni verranno eseguite sul database `negozio`.

## Creazione di una Tabella

Per creare una tabella si utilizza il comando `CREATE TABLE`:

```sql
CREATE TABLE nome_tabella (
    colonna1 tipo1 attributi,
    colonna2 tipo2 attributi,
    ...
);
```

Esempio:

```sql
CREATE TABLE clienti (
    id INT AUTO_INCREMENT PRIMARY KEY,
    nome VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    telefono VARCHAR(20)
);
```

Questa tabella `clienti` contiene un ID univoco, un nome, un'email unica e un numero di telefono.

## Inserimento di Dati

Per inserire dati in una tabella si usa `INSERT INTO`:

```sql
INSERT INTO nome_tabella (colonna1, colonna2, ...) VALUES (valore1, valore2, ...);
```

Esempio:

```sql
INSERT INTO clienti (nome, email, telefono) VALUES ('Mario Rossi', 'mario@example.com', '1234567890');
```

## Selezione di Dati

Per visualizzare i dati di una tabella si usa `SELECT`:

```sql
SELECT colonna1, colonna2 FROM nome_tabella;
```

Esempio:

```sql
SELECT nome, email FROM clienti;
```

Questo comando mostra tutti i nomi e le email della tabella `clienti`.

## Aggiornamento di Dati

Per modificare dati esistenti si usa `UPDATE`:

```sql
UPDATE nome_tabella SET colonna1 = nuovo_valore WHERE condizione;
```

Esempio:

```sql
UPDATE clienti SET telefono = '0987654321' WHERE nome = 'Mario Rossi';
```

Questo aggiorna il numero di telefono del cliente `Mario Rossi`.

## Eliminazione di Dati

Per eliminare dati da una tabella si usa `DELETE`:

```sql
DELETE FROM nome_tabella WHERE condizione;
```

Esempio:

```sql
DELETE FROM clienti WHERE nome = 'Mario Rossi';
```

Questo elimina il cliente `Mario Rossi` dalla tabella `clienti`.

## Eliminazione di una Tabella

Per rimuovere una tabella si usa `DROP TABLE`:

```sql
DROP TABLE nome_tabella;
```

Esempio:

```sql
DROP TABLE clienti;
```

Questo comando elimina completamente la tabella `clienti`.

## Eliminazione di un Database

Per cancellare un intero database si usa `DROP DATABASE`:

```sql
DROP DATABASE nome_database;
```

Esempio:

```sql
DROP DATABASE negozio;
```

Questo elimina il database `negozio` e tutte le sue tabelle.

## Filtrare i Risultati

Si possono filtrare i risultati con `WHERE`:

```sql
SELECT * FROM nome_tabella WHERE condizione;
```

Esempio:

```sql
SELECT * FROM clienti WHERE email LIKE '%@gmail.com';
```

Questo seleziona tutti i clienti con email di Gmail.

## Ordinare i Risultati

Per ordinare i dati si usa `ORDER BY`:

```sql
SELECT * FROM nome_tabella ORDER BY colonna ASC|DESC;
```

Esempio:

```sql
SELECT * FROM clienti ORDER BY nome ASC;
```

Ordina i clienti in ordine alfabetico crescente per nome.

## Contare i Record

Per contare i record in una tabella si usa `COUNT`:

```sql
SELECT COUNT(*) FROM nome_tabella;
```

Esempio:

```sql
SELECT COUNT(*) FROM clienti;
```

Questo mostra il numero totale di clienti nella tabella.

## Calcolare la Media

Per calcolare la media di una colonna numerica si usa `AVG`:

```sql
SELECT AVG(colonna) FROM nome_tabella;
```

Esempio:

```sql
SELECT AVG(prezzo) FROM prodotti;
```

Questo calcola il prezzo medio dei prodotti nella tabella `prodotti`.

## Utilizzo di NOT IN

Per escludere specifici valori si usa `NOT IN`:

```sql
SELECT * FROM nome_tabella WHERE colonna NOT IN (valore1, valore2, ...);
```

Esempio:

```sql
SELECT * FROM clienti WHERE nome NOT IN ('Mario', 'Giulia');
```

Questo seleziona tutti i clienti tranne quelli con nome `Mario` o `Giulia`.

## Condizioni con AND e OR

Si possono combinare condizioni con `AND` e `OR`:

```sql
SELECT * FROM nome_tabella WHERE condizione1 AND condizione2;
SELECT * FROM nome_tabella WHERE condizione1 OR condizione2;
```

Esempio:

```sql
SELECT * FROM clienti WHERE nome = 'Mario' AND email LIKE '%@gmail.com';
SELECT * FROM clienti WHERE nome = 'Mario' OR nome = 'Giulia';
```

La prima query seleziona i clienti con nome `Mario` e email di Gmail, la seconda seleziona i clienti con nome `Mario` o `Giulia`.

## Utilizzo di LEFT JOIN

Per combinare i dati di più tabelle si usa `LEFT JOIN`:

```sql
SELECT colonne FROM tabella1 LEFT JOIN tabella2 ON tabella1.colonna = tabella2.colonna;
```

Esempio:

```sql
SELECT clienti.nome, ordini.id FROM clienti LEFT JOIN ordini ON clienti.id = ordini.id_cliente;
```

Questa query mostra tutti i clienti e, se presenti, i loro ordini, includendo anche i clienti senza ordini.

