# cpanel-domainparking
These two steps will allow you to enable your cPanel DNS Only hosts as a domain parking provider for domain names pointed to your name servers. You can customise the template with your own name servers, time to live, abuse contact and parking IP.

Once your domain names are pointed to a host you can then create a web page that can read the domain name and display this on screen with either adverts or other information as you wish. Remember to ensure the web server serving these pages has no hostname set in Apache. This will only answer over http:// not https://.

Support the request at cPanel at URL -
https://features.cpanel.net/topic/22062-domain-parking-for-any-domain-set-to-name-servers

# DNS Server Configuration
<b>Addition of the following to named.conf and named.conf.prerebuilddnsconfig<b>

<br>
<i>zone "." {<br>
type master;<br>
file "/etc/bind/domain.parking";<br>
};</i><br>

# Zone Configuration
<b>Zone configured with the following -</b><br>
<i>File:</i> /usr/named/domain.parking
<br><br>
<i>; Domain Parking Template V1.0<br>
@ IN SOA ns.yourbrand.co. abuse.yourbrand.co.uk. (<br>
86400 ; refresh, seconds<br>
7200 ; retry, seconds<br>
1209600 ; expire, seconds<br>
300 ) ; minimum, seconds<br>
<br>
; Name Servers<br>
300 IN NS ns.youbrand.co.<br>
300 IN NS ns.yourbrand.co.uk.<br>
300 IN NS ns.yourbrand.uk.<br>
300 IN NS ns.yourband.io.<br>
300 IN NS ns.yourband.tech.<br>
<br>
; Domain Parking<br>
* 300 IN A 8.8.8.8<br></i>
<br>
<br>
# Verification of Legitamite Domain Lookup<br>
<img src="https://raw.githubusercontent.com/1ClickServicesLtd/cpanel-domainparking/main/Verify.png">
<br>
<br>
# Confirmation of DNS Response using "Google.com"<br>
<img src="https://raw.githubusercontent.com/1ClickServicesLtd/cpanel-domainparking/main/Lookup.png">
