## Design Url Shortner ( bitly.com )
Design a scalable url shortner service platform like bitly.com or tinyurl.com. It should be scalable that means it should be highly available and should able to handle an increasing concurrent workload by adding more resources to the system.

### Doubts
**What would be the expiry of short url?**
**Ans:** It should remain in system forever.

**Can use create their custom random string for url? What will be maximum length of random string in url?**
**Ans:** Yes, customer can create their own random string in url with maximum limit of 16 character.

**How many url shortning requests expected per month?**
**Ans:** On average 100 million per month.

**Do we expect to provide metrics like analysis of per url**
**Ans:** Yes

### Requirements
* After giving long URL, service should generate a short & unique random alias for it.
* When visit a short URL, service should redirect to the long URL.
* QR code should generate while creating short url.
* System should persist url forever.
* Shortened link should be as small as possible & should not be guessable.
* Analytics dashboard for monitoring purpose.

### Non-Functional Requirements
* The system should be highly available. Because in case service goes down, all the url redirection will fail. The requests comming to the system should be succeed 99.99%.
* Redirection to the long URL should be happen with minimum latency.
* Service should provide REST API so that customers can integrate with other applications.


### References:
System Design – URL Shortening Service
https://www.geeksforgeeks.org/system-design-url-shortening-service

How to design a tiny URL or URL shortener?
https://www.geeksforgeeks.org/how-to-design-a-tiny-url-or-url-shortener

How a URL Shortening Application Works
https://dzone.com/articles/how-a-url-shortening-application-works

System Design : Scalable URL shortener service like TinyURL
https://medium.com/@sandeep4.verma/system-design-scalable-url-shortener-service-like-tinyurl-106f30f23a82
