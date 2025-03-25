# Introduction To PHP

PHP, which stands for Hypertext Preprocessor, is a popular open-source, server-side scripting language designed primarily for web development. It is embedded within HTML code and executed on the server, generating dynamic web content that is then sent to the client's browser. PHP is widely used due to its simplicity, flexibility, and robust ecosystem.

**Key Features of PHP**
- **Server-Side:** Runs on the server (e.g., Apache, Nginx), not the client’s browser.
-   **Embedded in HTML:** PHP code is written inside ```<?php ... ?> ``` tags within HTML files.
- **Dynamic Content:** Enables websites to display content based on user input, database data, or other conditions.
- **Cross-Platform:** Works on various operating systems like Windows, Linux, and macOS.
- **Database Integration:** Strong support for databases like MySQL, PostgreSQL, and SQLite.
- **Open-Source:** Free to use, with a large community contributing to its development.

### Installation

- **Ubuntu**
```
sudo apt update
sudo apt upgrade
sudo add-apt-repository ppa:ondrej/php
sudo apt update
sudo apt install php8.4-common php8.4-cli php8.4-fpm php8.4-{curl,bz2,mbstring,intl}
```
```
php -v
```

