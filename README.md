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
