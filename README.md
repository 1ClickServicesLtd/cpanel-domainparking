# cpanel-domainparking
These two steps will allow you to enable your cPanel DNS Only hosts as a domain parking provider for domain names pointed to your name servers. You can customise the template with your own name servers, time to live, abuse contact and parking IP.

Support the request at cPanel at URL -
https://features.cpanel.net/topic/22062-domain-parking-for-any-domain-set-to-name-servers

# DNS Server Configuration
<b>Addition of the following to named.conf and named.conf.prerebuilddnsconfig<b>

<code>
zone "." {
type master;
file "/etc/bind/domain.parking";
};
</code>

# Zone Configuration
<b>Zone configured with the following -</b>
<i>File:</i> /usr/named/domain.parking

<code>
; Hooble Domain Parking Template V1.0
@ IN SOA ns.hooble.co. abuse.hooble.co.uk. (
86400 ; refresh, seconds
7200 ; retry, seconds
1209600 ; expire, seconds
300 ) ; minimum, seconds

; Name Servers
300 IN NS ns.hooble.co.
300 IN NS ns.hooble.co.uk.
300 IN NS ns.hooble.uk.
300 IN NS ns.hooble.io.
300 IN NS ns.hooble.tech.

; Domain Parking
* 300 IN A 185.103.119.76
</code>

# Verification of Legitamite Domain Lookup
<img src="https://raw.githubusercontent.com/1ClickServicesLtd/cpanel-domainparking/main/Verify.png">

# Confirmation of DNS Response using "Google.com"
<img src="https://raw.githubusercontent.com/1ClickServicesLtd/cpanel-domainparking/main/Lookup.png">
