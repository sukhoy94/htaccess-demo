# htaccess-demo
Project which describes thing we can do with .htaccess config file


# Redirects

## Redirect directive
```
Redirect [status] URL-path URL
```

Example:
```
Redirect 301 /page1.html /page2.html
```
It's good to mention that query string will be in redirect too.
/page1.html?test=1 -> this will be redirected to /page2.html?test=1

### Redirect without GET params:

Simply add question (?) mark to destination URL 
```
Redirect 301 /page1.html /page2.html?
```

## RewriteEngine & RewriteRule
```
RewriteEngine on
RewriteRule ^/?category/(.*)$ /new_category.html [R=301,L]
```

To use mod_rewrite with Apache, the rewrite engine needs to be activated with the RewriteEngine on directive.


Regular expression: 
```
^ - Beginning of string.
$ - End of string.
(.*) - A place holder for any string within a URL. The parentheses store the string in a variable.
$1 - A variable that allows access to cached values that are stored within parentheses.
```
### Flags

```
[L] flag - stop evaluating any other rule
[R] flag - as R=301 which sends a 301 "Moved Permanently" code
[NC] flag - stands for non case sensitive, match both upper and lower case versions
[QSA] flag - query string append
```

### Redirect only php files:
```
RewriteRule ^/?category/(.*\.php)$ /new_category_php.php [R=301,L]
```


### RewriteCond

%{HTTP_HOST} == 'example.com'
```
RewriteCond %{HTTP_HOST} example.com$
```
