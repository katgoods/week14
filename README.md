# week14
## Unit 14 Homework: Web Development

### Instructions

In this homework, we will review the many of the concepts and tools covered in the web development unit. If needed, refer to the [HTTP](./HTTP_Reference.md) and [curl](./cURL_Reference.md) reference sheets provided to you.

For submission, create a new file containing the answers to the question.

#### HTTP Requests and Responses

Answer the following questions about the HTTP request and response process.

1. What type of architecture does the HTTP request and response process occur in?
    Client-Server Architecture

2. What parts make up an `HTTP request`?
    - Request line
    - Headers 
    - White space
    - Request body (optional)

3. What is the optional part of an HTTP request?
    - Request body (optional): Helps the server process the request correctly.

4. What three parts make up an HTTP response?
    - Response Status Line
    - Response Header 
    - Response Body

5. Which number class of status codes represent errors?
    - 400's and 500's

6. What are the two most common request methods that a security professional will come across?
    - Get
    - Post

7. Which type of HTTP request method is used for sending data?
    - Post (sends new data).

8. Which part of an `HTTP request` contains the data being sent to the server?
    - Headers

9. In which part of an HTTP response would the browser receive the web code to generate and style a web page?
    - Content-Type

#### Using cURL

Answer the following questions about `curl`:

10. What are the advantages of using curl over the browser?
    - It uses one of the supporting protocols without user interaction. So if you're looking for a container with no UI, you can use curl in the commandline.

11. Which curl option is used to change the request method?
    - curl --request www.website.com

12. Which curl option is used to set request headers?
    - curl -v -H ...

13. Which curl option is used to view the response header?
    - curl -I www.website.com

14. Which request method might an attacker use to scope out usable HTTP requests that an HTTP server will accept?
    - curl -v www.website.com

#### Sessions and Cookies

Recall that HTTP servers need ways to recognize clients from one another. These are implemented through sessions and cookies.

Answer the following questions about sessions and cookies.

15. Which response header sends a cookie to the client?

    ```HTTP
    HTTP/1.1 200 OK
    Content-type: text/html
    Set-Cookie: cart=Bob
    ```
    - Set-Cookie: cart=Bob

16. Which request header sets a cookie in the client?

    ```HTTP
    GET /cart HTTP/1.1
    Host: www.example.org
    Cookie: cart=Bob
    ```
    - Cookie: cart=Bob

#### Example HTTP Requests and Responses

Look through the following example HTTP request and response and answer the following questions.

#### HTTP Request Example

```HTTP
POST /login.php HTTP/1.1
Host: example.com
Accept-Encoding: gzip, deflate, br
Connection: keep-alive
Content-Type: application/x-www-form-urlencoded
Content-Length: 34
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Linux; Android 6.0; Nexus 5 Build/MRA58N) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/80.0.3987.132 Mobile Safari/537.36

username=Barbara&password=password
```

17. What was the request method?
    - Post

18. Was the request encrypted or unencrypted?
    - Unencrypted (not HTTPS)

19. Does the request have a user session associated to it?
    - Yes

20. What kind of data is being sent from this request body.
    - Login information

#### HTTP Response Example

```HTTP
HTTP/1.1 200 OK
Date: Mon, 16 Mar 2020 17:05:43 GMT
Last-Modified: Sat, 01 Feb 2020 00:00:00 GMT
Content-Encoding: gzip
Expires: Fri, 01 May 2020 00:00:00 GMT
Server: Apache
Set-Cookie: SessionID=5
Content-Type: text/html; charset=UTF-8
Strict-Transport-Security: max-age=31536000; includeSubDomains
X-Content-Type: NoSniff
X-Frame-Options: DENY
X-XSS-Protection: 1; mode=block

[page content]
```

21. What was the response status code?
    - 200 OK

22. Was the response encrypted or unencrypted?
    - Unencrypted

23. Does this response have a user session associated to it?
    - Yes (SessionID=5)

24. What kind of content is likely to be in the [page content] response body?
    - Text/html

25. If your class covered security headers, what security request headers have been included?
    - Strict-Transport-Security: max-age=31536000; includeSubDomains

#### Monoliths and Microservices

Answer the following questions about monoliths and microservices:

26. What are the individual components of microservices called?
    - Front-end server
    - Back-end server
    - Database

27. What is a service that writes to a database and communicates to other services?
    - Back-end server

28. What type of underlying technology allows for `microservices` to become scalable and have redundancy?
    - Containers allow microservices to become scalable and redundant. Containers aren't resource heavy and are easy to deploy. The fact that they are separated from each other allows one to continue working if another container goes down. 

#### Container Vulnerability Filtering

Answer the following questions about vulnerability filtering `Trivy` scans with `jq`:

29. Do `microservices` share the same kind of vulnerabilities as regular operating systems?
    - Not really. Microservices are separate compnents, which allows for different levels of security in each area. However, that security still requires proper configuration.

30. Would an organization be more concerned with `Low` severity vulnerabilities as much as `Critical`?
    - They should be. 'low' severity attacks can be combined with other attacks. Some attacks considered low severity include cookie persistence, grabbing version numbers of applications; an attacker could carry out a low-level attack just to get an error message that might reveal more information about the servers.

31. Would the bash tool `jq` be useful in finding certain kinds of vulnerabilities within a vulnerability report?
    - Yes. Jq is the command line tool that inspects .json files and helps parse out data and search for specified information.

#### Deploying and Testing a Container Set

Answer the following questions about multi-container deployment:

32. What is a tool that can be used to deploy multiple containers at once?
    - Docker allows you to deploy multiple containers at once.

33. What kind of file format was required for us to deploy a container set?
    - .yml files using ansible-playbook command.

#### Container Runtime Intrusion Detection Systems

34. What is a tool used to actively detects intrusion behavior within containers?
    - Falco is one (open-source CIDS alert tool).

35. What high-value system file might an intruder view that would trigger a `sensitive file opening` alert?
    - /etc/shadow

36. What kind of intruder action might trigger an alert from a container IDS that says `shell configuration file has been modified`?
    - Adding a user.

---

© 2020 Trilogy Education Services, a 2U, Inc. brand. All Rights Reserved.
