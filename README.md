
---

# Simple PHP S3 Server

A lightweight PHP server that mimics basic **Amazon S3 API behavior**, allowing you to store, retrieve, and serve files using simple HTTP requests.
This is useful for testing, development, or running your own minimal S3-like file storage without relying on AWS.

---

## ✨ Features

* Basic implementation of **S3 REST API** in PHP.
* Handles **PUT, GET, DELETE** requests for objects.
* Uses the local file system as backend storage.
* No external dependencies required.
* Easy to deploy on any PHP hosting.

---

## 📂 How It Works

* Buckets are represented as directories inside a root folder (`data/` by default).
* Objects (files) inside buckets are stored as regular files.
* Requests follow the S3 style:

  * `PUT /bucket-name/object.txt` → uploads an object.
  * `GET /bucket-name/object.txt` → retrieves an object.
  * `DELETE /bucket-name/object.txt` → deletes an object.
* Responses mimic S3 XML responses for compatibility.

---

## 🚀 Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/hochenggang/simple-php-s3-server.git
   cd simple-php-s3-server
   ```

2. Make sure the `data/` directory is writable:

   ```bash
   chmod -R 777 data
   ```

3. Deploy the project to your PHP hosting (Apache, Nginx, or shared hosting).

   * Upload all files via FTP/SCP or push via Git if supported.
   * Ensure PHP 7.4+ is enabled.

4. Access the server through your domain:

   ```
   http://your-domain.com/bucket-name/object.txt
   ```

---

## 🛠️ Running Locally with PHP Built-in Server

For quick testing:

```bash
php -S localhost:8000 -t .
```

Then test with `curl`:

```bash
# Upload file
curl -X PUT --data-binary @test.txt http://localhost:8000/mybucket/test.txt

# Retrieve file
curl http://localhost:8000/mybucket/test.txt

# Delete file
curl -X DELETE http://localhost:8000/mybucket/test.txt
```

---

## 🌍 Deployment to Hosting

### Option 1: Shared Hosting (cPanel, etc.)

* Upload all repository files to your hosting root.
* Set `public_html` (or equivalent) as the document root.
* Ensure `data/` folder is writable (set permissions in File Manager or SSH).

### Option 2: VPS / Cloud Server

* Install Apache or Nginx with PHP support.
* Point your virtual host root to the project folder.
* Restart the web server.

Example for Apache:

```apache
<VirtualHost *:80>
    ServerName your-domain.com
    DocumentRoot /var/www/simple-php-s3-server
    <Directory /var/www/simple-php-s3-server>
        AllowOverride All
        Require all granted
    </Directory>
</VirtualHost>
```

---

## ✅ Example Usage

```bash
# Create bucket by uploading a file
curl -X PUT --data-binary @hello.txt http://your-domain.com/demo-bucket/hello.txt

# Get file
curl http://your-domain.com/demo-bucket/hello.txt

# Delete file
curl -X DELETE http://your-domain.com/demo-bucket/hello.txt
```

---

## ⚠️ Notes

* This is a **simplified S3 server** for development/testing only.
* Not production-grade: no authentication, no SSL handling, no advanced features.
* Ensure your hosting environment has proper permissions and security in place.

---
