## Purpose
This repository was created to simplify the SWF-based JSON CSRF exploitation. It should work also with XML data using optional parameters.

## Instructions
The .swf file take 4 parameters:
1) **jsonData** - apparently, JSON Data:) Can be other type of data, if optional `ct` param specified.
2) **php_url** - URL of the 307 redirector php file.
3) **endpoint** - target endpoint, which is vulnerable to CSRF.
4) **ct** (optional) - specify your own Content-Type. Without this parameter it will be `application/json`

Place test.swf, test.php and crossdomain.xml on your host, then simply call the SWF file with the correct parameters.

Example call:
https://yourhost.com/test.swf?jsonData={"test":1}&php_url=https://yourhost.com/test.php&endpoint=https://targethost.com/endpoint

If you have the questions regarding this repository - ping me in the Twitter: https://twitter.com/h1_sp1d3r

## Thanks
Special thanks to the https://twitter.com/emgeekboy, who inspired me to make this repository.
Related blog posts about this: 
* http://www.geekboy.ninja/blog/exploiting-json-cross-site-request-forgery-csrf-using-flash/
* http://research.rootme.in/forging-content-type-header-with-flash/
* http://resources.infosecinstitute.com/bypassing-csrf-protections-fun-profit/#gref


## Disclaimer
This repository is made for educational and ethical testing purposes only. Usage for attacking targets without prior mutual consent is illegal.
By using this testing tool you accept the fact that any damage (dataleak, system compromise, etc.) caused by the use of this tool is your responsibility.

## FAQ
1. Can we read response from server?

 Answer: no. Because of SOP. Still, if crossdomain.xml on the target host exist, and misconfigured - in this case yes.
 
2. Does it work with requests other than GET/POST?

 Answer: no.
 
3. Does it possible to craft custom headers like X-Requested-With, Origin or Referrer?

 Answer: no (it was possible in the past, but not now). Still, if you will find other bug, for example, CRLF Injection, you can chain it with this CSRF trick.

## Commits, PRs and bug reports are welcome!
