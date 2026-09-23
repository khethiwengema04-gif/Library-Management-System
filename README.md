## LIBRARY MANAGEMENT SYSTEM(PostgreSQL)

//Project Description  

// CREATED TABLES: authors,books, patron

CREATE TABLE IF NOT EXISTS authors(
id INT,
name VARCHAR, 
nationality VARCHAR,
birth_year INT,
death_year INT
);

CREATE TABLE IF NOT EXISTS books (
    id INT PRIMARY KEY, 
    title VARCHAR(255), 
    author_id INT,
    genres TEXT[], 
    published_year INT,
	available BOOLEAN
);

CREATE TABLE IF NOT EXISTS patron (
    id INT PRIMARY KEY, 
    name VARCHAR(255),
    email VARCHAR(255),
    borrowed_books INT[]
);
//
