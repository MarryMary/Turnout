# Turnout PHP Routing System
Web routing system for PHP scripts.  
# Usage
  
## methods
Turnout router is having 5 methods.  
get, post, put, delete is symmetrical to HTTP methods.  
all is allow all access method.  
If not matched routing or method, they are returning false(bool type).  

* get()  
* post()  
* put()  
* delete()  
* all()  
  
## Arguments
All method arguments are common.  
1. routing  
  please hand over access route  
2. function  
  please hand over executable function.  
  If matched routing, execute it
  
## Normal routing
```php
Method::get('/', function(){ echo "hello, world!"; });
```  
This is the simplest example.  
If user access 「https://foo.bar/」, PHP is say「hello, world!」  

```php
Method::get('/hello/:sample', function($variables){ echo $variables['sample'] });
```  
In the following example, the parameter is received by URL.  
