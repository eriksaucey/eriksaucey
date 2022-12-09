Application Programming INterface

API
	Connect to other apps and communicate.
		Internal
		Mobile and Web Apps
How API based apps are different	
	Server is used as a proxy for data
	The client renders the component, not the server
	Clients consume raw data
	APIs expose underlying implementation of the app
	THe user's state is usually maintained and monitored by the client
	More param,eters are sent in each HTTP request (objects, filters)

Vulnerabilities:
	Traditional vulnerabilities are less common in API-Based Apps
			SQLi - Increasing use of ORMs
			CSRF - Authorization headers instead of cookies
			Path Manipulations - Cloud-Based storage
			Classsic IT Security Issues - SaaS
			