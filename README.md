# SMS Y4 RUPP

RosarioSIS-based Student Information System.

## Requirements

- PHP >= 8.0 with extensions: `pgsql`, `pdo_pgsql`, `mbstring`, `intl`, `curl`, `gd`, `zip`, `json`
- PostgreSQL >= 9.2

Check your PHP extensions:

```bash
php -m | grep -iE 'pgsql|mbstring|intl|curl|gd|zip'
```

## Setup

### 1. Clone the repo

```bash
git clone git@github.com:Houtkysopanha/sms-y4-rupp.git
cd sms-y4-rupp
```

### 2. Create the database

```bash
psql -U postgres -c "CREATE USER rosariosis_user WITH PASSWORD 'your_password';"
psql -U postgres -c "CREATE DATABASE rosariosis_db OWNER rosariosis_user;"
```

Load the schema and demo data:

```bash
psql -U postgres -d rosariosis_db -f rosariosis.sql
```

### 3. Configure the app

Copy the sample config and fill in your database credentials:

```bash
cp config.inc.sample.php config.inc.php
```

Edit `config.inc.php`:

```php
$DatabaseType     = 'postgresql';
$DatabaseServer   = 'localhost';
$DatabaseUsername = 'rosariosis_user';
$DatabasePassword = 'your_password';
$DatabaseName     = 'rosariosis_db';
```

`config.inc.php` is gitignored — never commit it, it holds real DB credentials.

### 4. Run the app locally

```bash
php -S localhost:8080
```

Visit **http://localhost:8080**.

## Default logins (demo data)

| Username | Password | Role          |
|----------|----------|---------------|
| `admin`  | `admin`  | Administrator |
| `teacher`| `teacher`| Teacher       |
| `parent` | `parent` | Parent        |

Change these before using real student data.

## Notes

- Full upstream install docs: [INSTALL.md](INSTALL.md)
- License: [GPL-2.0](LICENSE)
