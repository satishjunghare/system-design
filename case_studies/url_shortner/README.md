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


### Capacity Estimation and Constraints in URL Shortening Service
Now we know our system will generate around 100 millions short urls per month and on this basis we have to estimate following things...
* Throughput ( QPS for read and write queries )
* What will be the ratio of Read/Write
* Expected latency from the system
* Storage estimation
* Trafic estimation for both Read/Write queries
* Memory estimation
  * If we are using cache, then how much data we are going to store in cache
  * How much data we want to store in persistent storage (Disk/SSD)?
  * How much Memory(Ram) we require to achieve this?

#### Trafic Estimation Of Write Operations:
We have considered that system will generate 100 Millions of records per month and we are going to store that much records for next 100 years.

**Write Requests Estimation**
**Per second:** 100 Millions / (30 Days * 24 Hours * 3600 Seconds) = 40 URLs/Second
**For 1 month:** 100 Millions
**For 1 year:** 100 Millions * 12 Months = 1.2 Billions
**For 100 years:** 1.2 Billions * 100 Years = 120 Billions


#### Storage Estimation:
Here each write request will genrate one short url to be store in persistent storage for long time. Lets assume each record takes nearby 500 Bytes of space in storage. Then how much storage capacity we required to store for different time span?

**For 1 month:** 100 Millions * 500 Bytes = 50GB
**For 1 year:** 50GB * 12 Months = 600GB
**For 100 years:** 600GB * 100 Years = 60TB

These amount of storage capacity we will require to store records. As soon as we store single url record, multiple users are going to access that short url. Here we store once but access multiple times by multiple users. Therefore the trafic of reading operation is always going to higher than write operation.

#### Trafic Estimation Of Read Requests
Lets assume 100 users are going to read a single url, so the number of total urls will be redirect/read per second is **(100*40) = 4000/sec**

It would be always bad idea if we are going to send such a huge trafic to the persistent database to fetch the records every time. When the trafic in a perticular URL is very high, system should send them to the cache memory(since cache memory is faster) to read. Before start using memory, we need to have clear idea on how much data we are going to store in memory.

#### Memory Estimation:



### References:

System Design – URL Shortening Service
https://www.geeksforgeeks.org/system-design-url-shortening-service

How to design a tiny URL or URL shortener?
https://www.geeksforgeeks.org/how-to-design-a-tiny-url-or-url-shortener

How a URL Shortening Application Works
https://dzone.com/articles/how-a-url-shortening-application-works

System Design : Scalable URL shortener service like TinyURL
https://medium.com/@sandeep4.verma/system-design-scalable-url-shortener-service-like-tinyurl-106f30f23a82
