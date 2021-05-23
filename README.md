# Aplikasi Barang Masuk & Keluar

Features
-------------
- Login
- Barang
- Category Barang
- Barang Masuk
- Barang Keluar
- Laporan Stock Barang
- Laporan Barang Masuk
- Laporan Barang Keluar
-------------

Installation
-------------
`git clone https://github.com/drbarazi/app-importir.git`

`cd importir`

`composer install`

`cp .env.example .env`

`php artisan key:generate`

`php artisan jwt:secret`

`php artisan migrate`

`php artisan db:seed`

-------------

API Documentation
-------------
> You can import my postman_collection.json to your postman or you can follow documentation bellow

### Authentications

#### Login
```
    [POST] => {{siteUrl}}/api/auth/login
    header {
        "Content-Type": "application/json"
        "Accept": "application/json"
    }
	
	/* 
        staff@mail.com (email untuk staff) 
        staff1234 (password untuk staff) 
	*/
	
    body {
        "email": "admin@mail.com", 
        "password": "admin1234"
    }
```
### Logout

```
    [POST] => {{siteUrl}}/api/auth/logout
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }
```

-------------

## Categories

### List

```
    [GET] => {{siteUrl}}/api/categories
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }
```

### Create

```
    [POST] => {{siteUrl}}/api/categories
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }

    body {
        "name": "Ex. Category"
    }
```

### Update

```
    [PUT] => {{siteUrl}}/api/categories/{id}
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }

    body {
        "name": "Ex. New Category"
    }
```

### Delete

```
    [DELETE] => {{siteUrl}}/api/categories/delete/{id}
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }
```

-------------


## Items

### List

```
    [GET] => {{siteUrl}}/api/items
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }
```

### Create

```
    [POST] => {{siteUrl}}/api/items
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }

    body {
        "name": "Ex. Item",
        "code": "Ex. code",
        "category_id": 3
    }
```

### Update

```
    [PUT] => {{siteUrl}}/api/items/{id}
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }

    body {
        "name": "Ex. Item",
        "code": "Ex. code",
        "category_id": 2
    }
```

### Delete

```
    [DELETE] => {{siteUrl}}/api/items/{id}
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }
```

-------------

## Transactions

### Incoming Item

```
    [POST] => {{siteUrl}}/api/transactions/in
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }

    body {
        "item_id":3,
        "quantity":40,
        "entry_date":"2021-05-01"
    }
```

### Outcoming Item

```
    [POST] => {{siteUrl}}/api/transactions/out
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }

    body {
        "item_id":5,
        "quantity":13,
        "entry_date":"2021-03-08"
    }
```

-------------

## Report

### Stock

```
    [POST] => {{siteUrl}}/api/reports/stock
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }
    
    /*
        type = day, month, week, or year
    */
    body {
        "type":"year",
        "date":"2021-04-01"
    }
```

### Item In

```
    [POST] => {{siteUrl}}/api/reports/incoming
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }
    
    /*
        type = day, month, week, or year
    */
    body {
        "type":"week",
        "date":"2021-04-01"
    }
```

### Item Out

```
    [POST] => {{siteUrl}}/api/reports/outcoming
    header {
        "Content-Type": "application/json",
        "Accept": "application/json",
        "Authorization": "Bearer <token>"
    }
    
    /*
        type = day, month, week, or year
    */
    body {
        "type":"month",
        "date":"2021-04-01"
    }
```