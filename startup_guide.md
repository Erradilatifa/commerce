# Startup Guide: E-SHOP Laravel Project

This guide will walk you through the steps to get the project up and running on your local machine.

## Prerequisites
- **XAMPP** (or any server with PHP 8.1+ and MySQL/MariaDB)
- **Composer** (PHP dependency manager)
- **Node.js & NPM** (for frontend assets)

---

## 🚀 Getting Started

### 1. Database Configuration
Open your `.env` file and ensure the database credentials match your local MySQL setup:
```env
DB_CONNECTION=mysql
DB_HOST=127.0.0.1
DB_PORT=3306
DB_DATABASE=e-shop
DB_USERNAME=root
DB_PASSWORD=
```
> [!NOTE]
> Make sure you have created an empty database named `e-shop` in your phpMyAdmin.

### 2. Install Dependencies
Run these commands in your project root:
```bash
composer install
npm install
```

### 3. Setup Database and Data
Since the project comes with a pre-populated database dump, follow these steps to restore the tables and data:

1.  **Wipe existing tables** (if any):
    ```bash
    php artisan db:wipe
    ```
2.  **Import the SQL dump**:
    Import the file located at `database/e-shop.sql` using phpMyAdmin or your preferred MySQL client.
3.  **Run pending migrations**:
    ```bash
    php artisan migrate
    ```

### 4. Fix Image Storage
To make sure product images appear correctly, run:
```bash
php artisan storage:link
```
> [!IMPORTANT]
> Some database paths use `Product` (singular) while others use `Products` (plural). If images are still missing, ensure you have a link or junction between these folders in `storage/app/public/photos/1/`.

### 5. Start the Application
```bash
php artisan serve
```
Visit `http://localhost:8000` in your browser.

---

## 🔐 Credentials

### Admin Panel
- **URL**: `http://localhost:8000/admin`
- **Email**: `admin@gmail.com`
- **Password**: `1111`

### User Account
- **Email**: `user@gmail.com`
- **Password**: `1111`

---

## 🛠 Troubleshooting
- **Missing Images**: Ensure the `public/storage` symbolic link exists.
- **500 Error**: Run `php artisan key:generate` if it hasn't been done.
- **Database Error**: Double check your `DB_DATABASE` name in `.env`.
