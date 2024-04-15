---
title: "VARCHAR Vs. CHAR in SQL"
seoTitle: "VARCHAR vs CHAR in SQL: Understanding the Key Differences"
seoDescription: "Learn the distinctions between VARCHAR and CHAR in SQL databases. Choose between flexible VARCHAR or fixed-length CHAR for better data storage and retrieval"
datePublished: Mon Apr 15 2024 11:00:27 GMT+0000 (Coordinated Universal Time)
cuid: clv0ufvlc001u08jue2z434eu
slug: varchar-vs-char-in-sql
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1713115838265/05a1e25a-0ab3-4e01-b783-7e8bf8514d5c.jpeg
tags: backend, databases, sql

---

When you're setting up your database, picking the right datatype can make a big difference in how it performs and how much space it takes up. Two common choices for storing text data are VARCHAR and CHAR. They might seem similar, but they work differently under the hood. Let's break it down in simple terms with examples.

### What's VARCHAR?

Think of VARCHAR as a flexible friend. It's short for "variable character." When you use VARCHAR, you tell the database how long the longest string in that column can be. But here's the cool part: it only takes up as much space as it needs for each entry.

```sql
CREATE TABLE Employees (
    EmployeeID INT PRIMARY KEY,
    FirstName VARCHAR(50),
    LastName VARCHAR(50)
);
```

In this table, the names of employees can vary in length. VARCHAR lets us handle that easily.

### What's CHAR?

CHAR, on the other hand, is like a strict teacher. It stands for "character." When you use CHAR, you set a specific length for every entry in that column. Even if the actual data is shorter, it still fills up that space.

```sql
CREATE TABLE Products (
    ProductCode CHAR(8) PRIMARY KEY,
    ProductName VARCHAR(100),
    Price DECIMAL(10, 2)
);
```

Here, the product codes are always eight characters long. CHAR makes sure of that, adding spaces if needed.

### The Big Differences:

1. **Space Efficiency:**
    
    * VARCHAR saves space by using only what it needs for each entry.
        
    * CHAR takes up a fixed amount of space, even if the data is shorter.
        

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1713114770242/979ed9f0-b246-4a3d-b596-a703f6134648.png align="center")

1. **Speed:**
    
    * Retrieving data from CHAR columns can be a bit faster because all entries have the same length.
        
    * VARCHAR might take a tiny bit longer because the lengths can vary.
        
2. **Indexing and Searching:**
    
    * VARCHAR works well with indexing, especially for searches involving different length strings.
        
    * CHAR can be good for exact matches and comparisons because all entries are the same length.
        

### Choosing the Right One:

It depends on your data:

* Use VARCHAR for things like names or descriptions where the length varies.
    
* Use CHAR for things like codes or IDs where you want every entry to be the same length.
    

### Conclusion:

VARCHAR and CHAR have their strengths and weaknesses. VARCHAR is flexible, while CHAR is strict. By understanding how they work, you can make smarter choices when designing your database. So, pick the one that fits your data best, and you'll be on your way to a well-organized database!