This is an easy to use PHP/cURL class to handle most needed tasks
[official website](http://www.abdulibrahim.com/php-curl-class/)
<hr>
### Table of Contents
**[Installation](#installation)** <br>
**[To download file](#download--file)** <br>
**[Post Form](#post-form)** <br>
**[GET form](#get-form)** <br>
**[Retrieve Header](#retrieve-header)** <br>
**[basic authentication](#basic-authentication)** <br>
**[Returned Data](#returned-data)** <br>
**[Options](#options)** <br>

#How to examples
### Installation
To utilize this class, first import curl.class.php into your project, and require it.
```php
require_once ('curl.class.php');
```
### Download  file
```php
$curl = new Curl();
$curl->getFile('http://www.example.com');
$curl->file; // this will contain the fetched file

```

### Post Form
```php
include 'curl.class.php';
$curl = new Curl();
$data_array['code'] = '55445';
$data_array['session'] = time();
$data_array['zipcode'] = '52415';
$data_array['Submit'] = 'Submit';
$curl->postForm('http://www.webbotsspidersscreenscrapers.com/zip_code_form.php', $data_array);
```
so the $data_array **key** is the form field name and array **value** is set to the field value.
For examples.
$data_array['zipcode'] = '52415'; .
['zipcode']=> form field name '52415'=> form field value .
![data_array](https://raw.githubusercontent.com/abdul202/php-cURL-class/master/images/data_arrary.jpg)
### Get form
```php
include 'curl.class.php';
$curl = new Curl();
$data_array['term'] = 'games';
$data_array['sort'] = 'up';
$curl->getForm('http://www.webbotsspidersscreenscrapers.com/search/search.php', $data_array);
```
Submits a form with the GET method
### Retrieve Header
```php
include 'curl.class.php';
$curl = new Curl();
$curl->getHeader('http://www.example.com/');
```
in this case the request method is HEAD and no body is returned
### Basic authentication
```php
include 'curl.class.php';
$curl = new Curl();
$username = 'webbot';
$password = 'sp1der3';
$curl->basicAuth($username, $password);
$curl->getFile('http://www.webbotsspidersscreenscrapers.com/basic_authentication');
```
To login using basic authentication
### Returned Data
All of these examples will return 3 results <br>
##### 1- Contents of the fetched file
```php
$curl->file 
```
##### 2- Get information regarding a specific transfer
```php
$curl->infoArray 
```
it returns a lot of useful information as an associative array
##### 3-  return the last error generated by cURL
```php
$curl->error 
```
### Options
###### change agent name
the agent name to use instead of the default ( the default is set to Firefox )
```php
$curl->setAgent('your agent name')
```
###### Time out
Maximum time in seconds that you allow the whole operation to take (connection + files ) <br>
( the default is 25 seconds )
```php
$curl->setTimeOut()
```
###### Connection Time out
Maximum time in seconds that you allow curl's connection to take instead of the default (connection only) <br>
This only limits the connection phase <br>
( the default is 60 seconds )
```php
$curl->setConnectionTimeOut()
```
###### Cookie location
Location of your cookie file instead of the default <br>
( the default is cookie.txt ) to the script home directory )<br>
```php
$curl->setCookieFile()
```
the path you specify must be relative for example
if you have a folder named tmp and want the cookie to saved to this folder it will be like that<br>
example <br>
```php
$curl->setCookieFile('tmp/cookie.txt')
```
###### referer
the referer to use instead of the default (the default is https://www.google.com)
```php
$curl->setReferer()
```
###### Include header
to include response header with the body
```php
$curl->includeHeader() 
```
###### Verbose
To enable verbose which will write more details about the transfer
```php
$curl->enableVerbose()
```
To change the location of your Verbose file (the default is verbose.txt resides in the script home directory) <br>
the path you specify must be relative for example<br>
if you have a folder named tmp and want the verbose file to saved to this folder it will be like that <br>
example <br>
```php
$curl->setVerboseFile('tmp/cookie.txt')
```

###### Redirection limits
To change the max redirections (the default is 4)
```php
$curl->setMaxRedirections ($max)
```
###### Add Headers
An array of HTTP header fields to set
```php
$curl->addHeader ()
```
example
```php
$header_array[] = "Accept-Encoding: compress, gzip";
$curl->addHeader ($header_array);
```
Note that it expects to receive data in an array
