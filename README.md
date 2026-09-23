## LIBRARY MANAGEMENT SYSTEM(PostgreSQL)

<img src="https://socialify.git.ci/khethiwengema04-gif/Library-Management-System/image?language=1&owner=1&name=1&stargazers=1&theme=Light" alt="Library-Management-System" width="640" height="320" />

## Project Description 
The Library Management System is a relational database application developed using PostgreSQL to streamline library operations. The system is designed to manage a core collection of assets consisting of books, authors, and library patrons.
Created the database and the database name is LibraryDB. Then the is the the creation of the tables,inserting e.t.c, It supports full CRUD (Create, Read, Update, Delete) operations.

## CREATED TABLES: authors,books, patron
``` sql
CREATE TABLE IF NOT EXISTS authors(
id INT,
name VARCHAR, 
nationality VARCHAR,
birth_year INT,
death_year INT
);
```
``` sql
CREATE TABLE IF NOT EXISTS books (
    id INT PRIMARY KEY, 
    title VARCHAR(255), 
    author_id INT,
    genres TEXT[], 
    published_year INT,
	available BOOLEAN
);
```
``` sql
CREATE TABLE IF NOT EXISTS patron (
    id INT PRIMARY KEY, 
    name VARCHAR(255),
    email VARCHAR(255),
    borrowed_books INT[]
);
```
## Inserting the data in the database
``` sql
INSERT INTO authors (id, name, nationality, birth_year, death_year) VALUES
(1, 'George Orwell', 'British', 1903, 1950),
(2, 'Harper Lee', 'American', 1926, 2016),
(3, 'F. Scott Fitzgerald', 'American', 1896, 1940),
(4, 'Aldous Huxley', 'British', 1894, 1963),
(5, 'J.D. Salinger', 'American', 1919, 2010),
(6, 'Herman Melville', 'American', 1819, 1891),
(7, 'Jane Austen', 'British', 1775, 1817),
(8, 'Leo Tolstoy', 'Russian', 1828, 1910),
(9, 'Fyodor Dostoevsky', 'Russian', 1821, 1881),
(10, 'J.R.R. Tolkien', 'British', 1892, 1973);
```
``` sql
INSERT INTO books (id, title, author_id, genres, published_year, available) VALUES
(1, '1984', 1, ARRAY['Dystopian', 'Political Fiction'], 1949, TRUE),
(2, 'To Kill a Mockingbird', 2, ARRAY['Southern Gothic', 'Bildungsroman'], 1960, TRUE),
(3, 'The Great Gatsby', 3, ARRAY['Tragedy'], 1925, TRUE),
(4, 'Brave New World', 4, ARRAY['Dystopian', 'Science Fiction'], 1932, TRUE),
(5, 'The Catcher in the Rye', 5, ARRAY['Realist Novel', 'Bildungsroman'], 1951, TRUE),
(6, 'Moby-Dick', 6, ARRAY['Adventure Fiction'], 1851, TRUE),
(7, 'Pride and Prejudice', 7, ARRAY['Romantic Novel'], 1813, TRUE),
(8, 'War and Peace', 8, ARRAY['Historical Novel'], 1869, TRUE),
(9, 'Crime and Punishment', 9, ARRAY['Philosophical Novel'], 1866, TRUE),
(10, 'The Hobbit', 10, ARRAY['Fantasy'], 1937, TRUE);
```
``` sql
INSERT INTO patron (id, name, email, borrowed_books) VALUES
(1, 'Alice Johnson', 'alice@example.com', ARRAY[]::INT[]),
(2, 'Bob Smith', 'bob@example.com', ARRAY[1, 2]),
(3, 'Carol White', 'carol@example.com', ARRAY[]::INT[]),
(4, 'David Brown', 'david@example.com', ARRAY[3]),
(5, 'Eve Davis', 'eve@example.com', ARRAY[]::INT[]),
(6, 'Frank Moore', 'frank@example.com', ARRAY[4, 5]),
(7, 'Grace Miller', 'grace@example.com', ARRAY[]::INT[]),
(8, 'Hank Wilson', 'hank@example.com', ARRAY[6]),
(9, 'Ivy Taylor', 'ivy@example.com', ARRAY[]::INT[]),
(10, 'Jack Anderson', 'jack@example.com', ARRAY[7, 8]);
```
## READING THE OPERATIONS(QUERIES)
``` sql
SELECT * FROM books;

SELECT title FROM books;

SELECT * FROM books WHERE author_id = 2;

SELECT * FROM books WHERE available = TRUE;
```
## UPDATING THE OPERATIONS
``` sql
UPDATE books 
SET available = FALSE
WHERE id = 1;

UPDATE books
SET genres = array_append(genres, 'Classic')
WHERE title = '1984';

UPDATE patron 
SET borrowed_books = array_append(borrowed_books, 9)
WHERE id = 1
```
## DELETE OPERATION
``` sql
DELETE FROM books
WHERE title = 'Moby-Dick';

DELETE FROM authors
WHERE id = 5;
```
## ADVANCED QUERIES
``` sql
SELECT * FROM books
WHERE published_year > 1950;
```
``` sql
SELECT * FROM authors
WHERE nationality = 'American';
```
``` sql
UPDATE books
SET available = TRUE;
```
``` sql
SELECT * FROM books
WHERE available = TRUE 
AND published_year > 1950;
```
``` sql
SELECT * FROM authors
WHERE name ILIKE '%George%';
```
``` sql
UPDATE books
SET published_year = published_year +1
WHERE published_year = 1869;
```
