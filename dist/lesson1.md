# lesson 1

This [codewars.com kata](https://www.codewars.com/kata/514a024011ea4fb54200004b/solutions/python), is a simple exercise getting domain names from a url:
```
* url = "http://github.com/carbonfive/raygun" -> domain name = "github"
* url = "http://www.zombie-bites.com"         -> domain name = "zombie-bites"
* url = "https://www.cnet.com"                -> domain name = "cnet"
```

My approach was to conditionally remove the http:// string and www. string and then find the first period...

But the top solution leverages the fact that str.split(delimiter) will do nothing if the delimiter does not exist.

I love it.

```
# my solution
def domain_name(url):
    return url[(url.index("www.")+4 if "www." in url else url.index("//")+2 if "//" in url else 0):].split(".")[0]

# better solution
def domain_name(url):
    return url.split("//")[-1].split("www.")[-1].split(".")[0]
     
print(domain_name("www.xakep.co.uk"))
```

# lesson 2

This [kata](https://www.codewars.com/kata/526dbd6c8c0eb53254000110/train/python) asks you to ensure only alphanumeric characters and teaches two tricks.

```
 string.isalnum() # pythonic way to solve the problem
 re.compile('^[0-9a-zA-Z]+$').match(string) is not None
 # ^a == starts with a
 # a+ == undetermined multiples of a
 # a$ == ends with a
 # [0-9a-zA-Z] == one letter alphanumeric match group
 # r'^a+$' == true for "aaaaaaaaa" and "a"
```

```
import re

# my solution
def alphanumeric(password):
    return True if sum([0 if re.compile(r'[a-z]|[A-Z]|[0-9]').search(c) else 1 for c in password]) == 0 and len(password) > 0 else False

# re solution
def alphanumeric(string):
    return re.compile('^[0-9a-zA-Z]+$').match(string) is not None

# py solution
def alphanumeric(string):
    return string.isalnum()

print(alphanumeric("hello156789GHJ"))
```
# replit day 41

`dictionary.items() # returns array of form [[key:value],..]`
