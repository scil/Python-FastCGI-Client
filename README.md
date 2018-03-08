
#Python FastCGI Client

#####A `Python` FastCGI Client for directly access FastCGI web resource through `FastCGI`


AUTHOR & Email
================

wuyunfeng
    - wyfsky888@126.com


How use?(You should start your FastCGI Process)
========================

    from FastCGIClient import *
    client = FastCGIClient('127.0.0.1', 9000, 3000, 0)
	params = dict()
	documentRoot = "/Users/baidu/php_workspace"
	uri = "/echo.php"
	content = "name=john&address=beijing"
	params = {'GATEWAY_INTERFACE': 'FastCGI/1.0',
          'REQUEST_METHOD': 'POST',
          'SCRIPT_FILENAME': documentRoot + uri,
          'SCRIPT_NAME': uri,
          'QUERY_STRING': '',
          'REQUEST_URI': uri,
          'DOCUMENT_ROOT': documentRoot,
          'SERVER_SOFTWARE': 'php/fcgiclient',
          'REMOTE_ADDR': '127.0.0.1',
          'REMOTE_PORT': '9985',
          'SERVER_ADDR': '127.0.0.1',
          'SERVER_PORT': '80',
          'SERVER_NAME': "localhost",
          'SERVER_PROTOCOL': 'HTTP/1.1',
          'CONTENT_TYPE': 'application/x-www-form-urlencoded',
          'CONTENT_LENGTH': len(content)
          }
	client.request(params, content)
        

An example for Laravel project
============================

use the example on the same server with php-fpm. I failed to use it on another machine with php-fpm listening all addreses.

```python
from FastCGIClient import *

#client = FastCGIClient('192.168.1.102', 9000, 3000, 0)
client = FastCGIClient('127.0.0.1', 9000, 3000, 0)
params = dict()
documentRoot = "/vagrant/www/zc/public"
s = "/index.php"
uri = "/login"
content = ""
params = {'GATEWAY_INTERFACE': 'FastCGI/1.0',
      'REQUEST_METHOD': 'GET',
      'SCRIPT_FILENAME': documentRoot + s,
      'SCRIPT_NAME': s,
      'QUERY_STRING': '',
      'REQUEST_URI': uri,
      'DOCUMENT_ROOT': documentRoot,
      'DOCUMENT_URI':s,
      
      'SERVER_SOFTWARE': 'php/fcgiclient',
      
      'REMOTE_ADDR': '127.0.0.1',
      'REMOTE_PORT': '9985',
      
      'SERVER_ADDR': '127.0.0.1',
      'SERVER_PORT': '80',
      'SERVER_NAME': "i",
      'SERVER_PROTOCOL': 'HTTP/1.1',
      'CONTENT_TYPE': 'application/x-www-form-urlencoded',
      'CONTENT_LENGTH': len(content)
      }

r= client.request(params, content)
print(r)

#with open('/vagrant/cig.html','wb') as f:
 #   f.write(r)
    


```

