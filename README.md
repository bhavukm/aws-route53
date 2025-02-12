AWS Route53 is the DNS (Domain Name System) service in AWS.

**DNS**, or the Domain Name System, translates human readable domain names (for example, www.amazon.com) to machine readable IP addresses (for example, 192.168.2.24).
Generally speaking, there are 4 types of DNS Nameservers: DNS Recursive Resolver (ISP), DNS Root Name Server, TLD (Top Level Domain) Name Server, and Authoritative Name Server.

**DNS Architecture:**

![image](https://github.com/user-attachments/assets/c7af43b8-bb42-4ca8-8fad-5bd091401974)

**Workflow:**

1. When the user puts the website name (www.example.com) in the browser, a DNS query is generated and routed to the DNS Recursive Resolver or we can say the ISP (Internet Service Provider), for example, a Broadband (WiFi) service provider. The ISP has its own DNS cache. This cache stores DNS information for any query that reached it in the past. It is stored for the TTL (Time To Live) that is specified. If the Recursive Resolver has the information then it is passed to the browser and the user is able to access the website.
   
2. In case, the DNS Recursive resolver does not have the information, then the query is forwarded to the DNS Root Name Server to find the information of the TLD (Top Level Domain) Name Server (NS) for that domain (example: ".com").

3. The TLD information is received by the recursive resolver.

4. The recursive resolver then forwards the query now to the TLD name server. The TLD name server finds out the information of the Authoritative Name Server (these can be multiple as well). The authoritative name server is the final destination where the website to IP information can be found. The information is stored in a Hosted Zone on this server.

5. The Authoritative name server name(s) is sent back to the recursive resolver.

6. The recursive resolver now sends the query to the authoritative name server.

7. The authoritative name server looks up the information in its hosted zone and sends it back to the recursive resolver.

8. The recursive resolver sends the website mapping information to the user's browser. Also, it caches that information for the Time To Live (TTL).

9. The user is now able to access the website: www.example.com

AWS Route53 Concepts:

This 53 represents the standard port for DNS service. Highly available, scalable DNS service. Basically, route53 can perform 3 functions:

Domain Registration, DNS Routing, and health checking

A general Route53 scenario:

![image](https://github.com/user-attachments/assets/0735a99f-154b-4540-bbbd-8102afff6e79)

DNS Terms:

CNAME (Canonical Name):  is a type of DNS record that points a subdomain to a fully qualified domain name (FQDN). Example: shown above

Name server (NS): is a server on the internet that's specialized in handling queries regarding the location of a domain name’s various services. If you set up your domain in Amazon Route 53, a list of name servers are already assigned to your domain.

A Record: Domain to IPV4 address mapping.

AAAA Record: Domain to IPV6 address mapping.

TLD (Top Level Domain): The highest level in the DNS structure which comes after dot, like .com

DNS Root Server: First stop in the DNS lookup.

![image](https://github.com/user-attachments/assets/1be0053c-f6d2-4624-a109-4f242deae987)

Authoritative nameserver: A vital part of DNS that makes it possible to access websites.

Top Level Domain (TLD): Generic part of the domain name. Example: .com, .org, .gov etc.

FQDN (Fully Qualified Domain Name):  are made up of multiple levels, including the subdomain, domain name, and top-level domain (TLD). 

![image](https://github.com/user-attachments/assets/79f60db2-5463-4a3b-ab01-d598ff3d9703)

More DNS Terms: https://www.opsschool.org/dns_101.html
