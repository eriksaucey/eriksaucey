1. Crawlers - Discover content through various means and index for Search engines
	1. Pure Discovery, - Indexes websites for search engine
	2. Following any URLs found from previously crawled websites. Traverse/Spreads like a virus
Attempt to traverse every URL and file that they can find.
![[4nrDDa0.png]]

![[nbbsAp4.png]]

![[CIM2c6N.png]] 
Recapping
![[Pasted image 20221005092555.png]]

When the search engine has some knowledge about keywords, teh crawler will crawl the domain containing "Pears".

Search Engine Optimization (SEO)

Abstract View: Search engines prioritise those domains that are easier to index.
	Factors
		1. Responsiveness of website to different browser types
		2. How easy it is to crawl your site
		3. Keywords the website has

SEO Checkup Tool
https://web.dev/measure/

Beepboop - Robots.txt

First thing indexed by crawlers when visiting a website
	-Serves as root directory
		Txt file defines the permissions of the crawler
		Specifies what files and directories can be crawled
______________________________________________________
	**Basic Example:**
		1  User-agent: *
		2  Allow: /
		3
		4  Sitemap: http://mywebsite.com/sitemap.xml
		5
		6
______________________________________________________
		A. Any Crawler can index the size
		B. The crawler can index the entire contents of the site
		C. The sitemap is located at http://mywebsite.com/sitemap.xml
		
Keywords and Functions

**User-agent** - Specify the type of "Crawler" that can index your site (the asterisk being a wildcard, allowing **all "User-agents"**

**Allow** - Specify the directories or file(s) that the "Crawler" **can** index

**Disallow** - Specify the directories or file(s) that the "Crawler" **cannot** index

**Sitemap** - Provide a reference to where the sitemap is located (improves SEO as previously discussed, we'll come to sitemaps in the next task)

________________________________________________
	**Only certain crawlers allowed Example:**
		1  User-agent: Googlebot
		2  Allow: /
		3
		4  User-agent: msnbot
		5  Disallow:  /
		6
		7
	____________________________
___________
