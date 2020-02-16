## d8-from-d7
# Migrate NJSGC from d8 to d7

This is code for the migrate module.  In addition, one needs to set up the .lando.yml with an additional database 
(do this before building the site) and then add to settings.php (do this after setting up Drupal 8 but BEFORE enabling the 
module).

Sample for settings.php (check lando info for actual settings):  
```php  
 $databases['db2']['default'] = array(  
  'database' => 'database',  
  'username' => 'mysql',  
  'password' => 'mysql',  
  'prefix' => '',  
  'host' => 'db2',  
  'port' => '3306',  
  'namespace' => 'Drupal\Core\Database\Driver\mysql',  
  'driver' => 'mysql',  
);

And this is where I named db2 in .lando.yml:

name: njmig  
recipe: drupal8  
config:  
  webroot: web  
services:  
  database:  
    portforward: 3307  
  db2:  
    type: mysql  
    portforward: 3308  
