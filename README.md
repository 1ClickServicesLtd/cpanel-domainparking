# cpanel-domainparking
These two steps will allow you to enable your cPanel DNS Only hosts as a domain parking provider for domain names pointed to your name servers. You can customise the template with your own name servers, time to live, abuse contact and parking IP.

Support the request at cPanel at URL -
https://features.cpanel.net/topic/22062-domain-parking-for-any-domain-set-to-name-servers

# DNS Server Configuration
<b>Addition of the following to named.conf and named.conf.prerebuilddnsconfig<b>

<code>
zone "." {<br>
type master;<br>
file "/etc/bind/domain.parking";<br>
};
</code>

# Zone Configuration
<b>Zone configured with the following -</b>
<i>File:</i> /usr/named/domain.parking

<code>
; Hooble Domain Parking Template V1.0<br>
@ IN SOA ns.hooble.co. abuse.hooble.co.uk. (<br>
86400 ; refresh, seconds<br>
7200 ; retry, seconds<br>
1209600 ; expire, seconds<br>
300 ) ; minimum, seconds<br>

; Name Servers
300 IN NS ns.hooble.co.<br>
300 IN NS ns.hooble.co.uk.<br>
300 IN NS ns.hooble.uk.<br>
300 IN NS ns.hooble.io.<br>
300 IN NS ns.hooble.tech.<br>
<br>
; Domain Parking<br>
* 300 IN A 185.103.119.76<br>
</code>
<br>
# Verification of Legitamite Domain Lookup<br>
<img src="https://raw.githubusercontent.com/1ClickServicesLtd/cpanel-domainparking/main/Verify.png">
<br>
# Confirmation of DNS Response using "Google.com"<br>
<img src="https://raw.githubusercontent.com/1ClickServicesLtd/cpanel-domainparking/main/Lookup.png">
