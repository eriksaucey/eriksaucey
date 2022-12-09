Framework written in Java that aims to provide web application penetration testing
	-also common with assessing mobile applications
Simplest Level:
	Burp captures and manipulates traffic between an attacker and the webserver
	-After capturing requests, we can choose to send them to various other parts of the framework

Burp Suite Pro - unrestricted version
	1. Automated vuln scanner
	2. Fuzzer/bruteforcer
	3. Saving projects
	4. Built in API to integrate with other tools
	5. Add new extensions for more functionality
	6. Access to Burp Suite Collaborator
Burp Suite Enterprise - used for continuous scanning.
	Web app scanner that periodically scans for vulns, similar to Nessus
	-Does not allow user to perform manual attacks
	-Sits on the server.

Tools in Community Edition
-   **Proxy:** The most well-known aspect of Burp Suite, the Burp Proxy allows us to intercept and modify requests/responses when interacting with web applications.
-   **Repeater:** The second most well-known Burp feature -- [Repeater](https://tryhackme.com/room/burpsuiterepeater) -- allows us to capture, modify, then resend the same request numerous times. This feature can be absolutely invaluable, especially when we need to craft a payload through trial and error (e.g. in an SQLi -- **S**tructured **Q**uery **L**anguage **I**njection) or when testing the functionality of an endpoint for flaws.
-   **Intruder:** Although harshly rate-limited in Burp Community, [Intruder](https://tryhackme.com/room/burpsuiteintruder) allows us to spray an endpoint with requests. This is often used for bruteforce attacks or to fuzz endpoints.
-   **Decoder:** Though less-used than the previously mentioned features, [Decoder](https://tryhackme.com/room/burpsuiteom) still provides a valuable service when transforming data -- either in terms of decoding captured information, or encoding a payload prior to sending it to the target. Whilst there are other services available to do the same job, doing this directly within Burp Suite can be very efficient.  
    
-   **Comparer:** As the name suggests, [Comparer](https://tryhackme.com/room/burpsuiteom) allows us to compare two pieces of data at either word or byte level. Again, this is not something that is unique to Burp Suite, but being able to send (potentially very large) pieces of data directly into a comparison tool with a single keyboard shortcut can speed things up considerably.  
    
-   **Sequencer:** We usually use [Sequencer](https://tryhackme.com/room/burpsuiteom) when assessing the randomness of tokens such as session cookie values or other supposedly random generated data. If the algorithm is not generating secure random values, then this could open up some devastating avenues for attack.

Very easy to write extensions with Java codebase
	Burp Suite Extender - quickly and easily uploads extensions to the framework
		-also provides a marketplace (BApp Store)
	Logger++ - Extends the logging functionality 