# Turnout PHP Routing System
Web routing system for PHP scripts.  
# Usage
please include composer's 「autoload.php」 and namespace 「Fratello\Henrietta\Router\Method」
  
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
If user access 「 http://localhost/ 」, PHP is say「hello, world!」  

## Parameter setting (Strict)
```php
Method::get('/hello/:sample', function($variables){ echo $variables['sample']; });
```  
You can get the URL parameter by prefixing it with ":" in the URL specification.  
If you set one argument to the anonymous function of the second argument, you can get an array of URL parameters whose argument is the word after:.  
Also, if the URL parameter is not included in the URL, it will be recognized that the URL does not match.  
If user access「 http://localhost/hello 」, routing not match.  
If user access「 http://localhost/hello/Test 」, PHP is say 「Test」.  

## Parameter setting (loose)
```php
Method::get('/hello2/?sample', function($variables){ 
    if(array_key_exists("sample", $value)){
        echo "あなたがURLに入れた文字は「".$value["sample"]."」です。";
    }else{
        echo "あなたはURLに何も入力しませんでした。";
    } 
});
```  
This example looks similar to the previous one, but a little different.  
By specifying the argument as "?" Instead of ":", access is possible even if the accessing user does not include the parameter in the URL.  
