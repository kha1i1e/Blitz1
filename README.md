# <ins>Blitz 1 Load Test Report</ins>

September 30, 2023

By:  Khalil Elkharbibi


### <ins>Overview</ins>

Nike has reached out to me regarding the URL shortener that I previously deployed on AWS Elastic Beanstalk. In their email, Nike expressed concerns raised by their customers about the extended duration it takes for their webpages to load. Nike's request is for us to minimize the latency that customers are currently encountering.

### <ins>Purpose</ins>

The purpose of Blitz 1 was to conduct a rigorous load test on the Python URL Shortening application deployed on AWS Elastic Beanstalk. This involved using Apache JMeter to simulate 1000 requests, allowing us to assess the application's performance and its infrastructure's ability to handle high traffic.


#### 1. <ins>Load Test Execution</ins>

During the blitz, I began by confirming the availability and accessibility of the Python URL Shortening application, hosted on an EC2 instance. Apache JMeter was configured to send 1000 requests to the application's URL simultaneously. Throughout this process, I closely monitored the application's response time to gauge the impact of these requests. It's important to note that both the URL shortening app and Apache JMeter were located in the AWS US East 1 region, a factor to consider when interpreting the results. After the test, I recorded a latency of approximately 41ms for the URL shortening app, compared to a pre-test latency of around 9ms.


#### 2. <ins>Addressing Latency Concerns</ins>

The observed latency during the load test raised concerns about the application's ability to handle increased user traffic effectively. To mitigate this latency and improve the URL shortening application's performance, I recommended implementing a Content Delivery Network (CDN). CDNs enhance performance by reducing latency to web applications through the distribution and caching of static and certain dynamic content on geographically distributed edge servers (data centers). I selected AWS CloudFront as the CDN solution for the URL shortening app, due to seamless integration with AWS Elastic Beanstalk, which simplified configuration and management. After configuration, AWS CloudFront provided a new URL for accessing the application, offering low-latency access to cached content. I then conducted another Apache JMeter load test, using the same parameters, against the new URL for the application. The latency for the URL shortening app, while utilizing AWS CloudFront, measured at approximately 9.65ms under the test load.


 | Latency Test Before Using AWS Cloudwatch CDN                 | Latency Test After Using AWS Cloudwatch CDN               |
 | ----------------------------------- | ----------------------------------- |
 | ![Screenshot 2023-09-30 015826](https://github.com/atlas-lion91/Blitz1/assets/140761974/50b1b2fc-98ec-4da8-9b78-6ae6d7fae57e) | ![Screenshot 2023-09-30 015145](https://github.com/atlas-lion91/Blitz1/assets/140761974/52c6847d-a2d9-4631-81ea-03b41cb6e2f8) |



#### 3. <ins>Primary Objective</ins>

The primary objective of this load testing scenario was to evaluate the performance of the Python URL Shortening application when exposed to a heavy traffic load. I initiated the process by establishing a foundational metric for the application's latency and subsequently subjecting it to stress testing. The insights gained from this testing informed our decision to enhance the application's infrastructure by introducing additional resources in the form of a CDN.



### <ins>Conclusion</ins>

In summary, the Blitz 1 load test has provided invaluable insights into the performance of the Python URL Shortening application. Through the strategic implementation of AWS CloudFront as our chosen Content Delivery Network (CDN), we have achieved a substantial reduction in latency, notably improving the application's response time by approximately 77%, from an initial measurement of 41ms to an impressive 9.65ms.

This enhancement is poised to significantly elevate the overall user experience, ensuring swift and efficient content delivery while effectively accommodating spikes in traffic. To maintain and further optimize this newfound level of performance, I would continue to prioritize ongoing monitoring and the exploration of potential enhancements. 
