# codewars lesson
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
