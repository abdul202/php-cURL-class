This is an easy to use PHP/cURL class to handle most needed tasks
<hr>
### Table of Contents
**[To download file](#to-download--file)** <br>
**[post Form](#post-form-data)** <br>
**[Return Header only](#to-get-only-header-response)** <br>
**[Submits a form with the GET method](#submits-a-form-with-the-get-method)** <br>
**[basic authentication](#to-login-using-basic-authentication)** <br>
**[Returned Data](#Returned-Data)** <br>
**[Options](#Options)** <br>

#How to examples

### To download  file
```
$curl = new Curl();
$curl->getFile('http://www.example.com');
$curl->file; // this will contain the fetched file

```

### post Form data
```
include 'curl.class.php';
$curl = new Curl();
$data_array['code'] = '55445';
$data_array['session'] = time();
$data_array['zipcode'] = '52415';
$data_array['Submit'] = 'Submit';
$curl->postForm('http://www.webbotsspidersscreenscrapers.com/zip_code_form.php', $data_array);
```
Every form data field have a name and value you wish to submit <br>
so the $data_array **key** is the form field name and array **value** is set to the field value <br>
for examples  <br>
$data_array['zipcode'] = '52415'; <br>
['zipcode']=> form field name '52415'=> form field value <br>
![data_array](https://raw.githubusercontent.com/abdul202/php-cURL-class/master/images/data_arrary.jpg)


### to get only header response
```
include 'curl.class.php';
$curl = new Curl();
$curl->getHeader('http://www.example.com/');
```
in this case the request method is HEAD and no body is returned
### Submits a form with the GET method
```
include 'curl.class.php';
$curl = new Curl();
$data_array['term'] = 'games';
$data_array['sort'] = 'up';
$curl->getForm('http://www.webbotsspidersscreenscrapers.com/search/search.php', $data_array);
```
### to login using basic authentication
```
include 'curl.class.php';
$curl = new Curl();
$username = 'webbot';
$password = 'sp1der3';
$curl->basicAuth($username, $password);
$curl->getFile('http://www.webbotsspidersscreenscrapers.com/basic_authentication');
```
### Returned Data
All of these examples will return 3 results <br>
##### 1- Contents of the fetched file
```
$curl->file 
```
##### 2- Get information regarding a specific transfer
```
$curl->infoArray 
```
it returns a lot of useful information as an associative array
##### 3-  return the last error generated by cURL
```
$curl->error 
```

### Options
###### change agent name
the agent name to use instead of the default ( the default is set to Firefox )
```
$curl->setAgent('your agent name')
```
###### Time out
how long to wait for a response from a server instead of the default ( the default is 25 seconds )
```
$curl->setTimeOut()
```
###### Cookie location
Location of your cookie file instead of the default <br>
( the default is cookie.txt ) to the script home directory )<br>
```
$curl->setCookieFile()
```
the path you specify must be relative for example
if you have a folder named tmp and want the cookie to saved to this folder it will be like that
```
$curl->setCookieFile('tmp/cookie.txt')
```
###### referer
the referer to use instead of the default (the default is https://www.google.com)
```
$curl->setReferer()
```
###### Include header
to include response header with the body
```
$curl->includeHeader() 
```
###### Verbose
To enable verbose which will write more details about the transfer
```
$curl->enableVerbose()
```
To change the location of your Verbose file (the default is verbose.txt resides in the script home directory) <br>
the path you specify must be relative for example<br>
if you have a folder named tmp and want the verbose file to saved to this folder it will be like that
```
$curl->setVerboseFile('tmp/cookie.txt')
```
example
```
$curl->setVerboseFile()
```
###### Redirection limits
To change the max redirections (the default is 4)
```
$curl->setMaxRedirections ($max)
```
An array of HTTP header fields to set
```
$curl->addHeader ()
```
example
```
$header_array[] = "Accept-Encoding: compress, gzip";
```
Note that it expects to receive data in an array.
