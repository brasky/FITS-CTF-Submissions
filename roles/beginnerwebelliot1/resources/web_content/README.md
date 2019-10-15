# PHP-Login

* There are four main pages: `login.php` shows the login form, `index.php` the default password-protected area, `logout.php` simply ends the session and `config.php` stores the user's information.

* If you want to password-protect any page, just add this snippet of code at the beginning of it:

```php
<?php
  session_start(); /* Starts the session */
  if($_SESSION['Active'] == false){ /* Redirects user to login.php if not logged in */
    header("location:login.php");
    exit;
  }
?>
```
