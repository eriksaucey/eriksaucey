Consist of a client and a server, where the clients request the server for a resource
Default Port: 80

Terms:
- Fully Qualified Domain Name (FQDN)
- Uniform Resource Locator (URL)

Resources over HTTP are accessed via a URL

HTTP Structure
--
![[Pasted image 20221207083040.png]]
| Component | Example | Description |
|--------------|------------|--------------------------------------|
| Scheme | `http://` `https://` | This is used to identify the protocol being accessed by the client, and ends with a colon and a double slash (`://`)
| User Info | `admin:password@` | This is an optional component that contains the credentials (separated by a colon `:`) used to authenticate to the host, and is separated from the host with an at sign (`@`)
| Host | inlanefreight.com | The host signifies the resource location. This can be a hostname or an IP address
| Port | :80 | The `Port` is separated from the `Host` by a colon (`:`). If no port is specified, `http` schemes default to port `80` and `https` default to port `443`
| Path | /dashboard.php | This points to the resource being accessed, which can be a file or a folder. If there is no path specified, the server returns the default index (e.g. `index.html`).
| `Query String` | `?login=true` | The query string starts with a question mark (`?`), and consists of a parameter (e.g. `login`) and a value (e.g. `true`). Multiple parameters can be separated by an ampersand (`&`).
| Fragments | #status | Fragments are processed by the browsers on the client-side to locate sections within the primary resource (e.g. a header or section on the page).

Not all components are required to access a resource. Mandatory fields include scheme and host

HTTP Flow![[Pasted image 20221207083929.png]]
cURL
--
Command line tool and library that primarily supports HTTP along with many other protocols.
-Essential for sending various types of web requests from the command line

```shell-session
eriksalcedo@htb[/htb]$ curl inlanefreight.com

<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
#...SNIP...

```

cuRl does not render the HTML/Javascript/CSS code. Instead prints it in raw format

-0 flag - output the content into a file. To specify the output file name, we can use the -o flag and specify the name.

```shell-session
eriksalcedo@htb[/htb]$ curl -O inlanefreight.com/index.html
eriksalcedo@htb[/htb]$ ls
index.html
```

To silence the status, use the -s flag

```shell-session
eriksalcedo@htb[/htb]$ curl -s -O inlanefreight.com/index.html
```

Use the -h flag to see other options

```shell-session
eriksalcedo@htb[/htb]$ curl -h
Usage: curl [options...] <url>
 -d, --data <data>   HTTP POST data
 -h, --help <category> Get help for commands
 -i, --include       Include protocol response headers in the output
 -o, --output <file> Write to file instead of stdout
 -O, --remote-name   Write output to a file named as the remote file
 -s, --silent        Silent mode
 -u, --user <user:password> Server user and password
 -A, --user-agent <name> Send User-Agent <name> to server
 -v, --verbose       Make the operation more talkative

This is not the full help, this menu is stripped into categories.
Use "--help category" to get an overview of all categories.
Use the user manual `man curl` or the "--help all" flag for all options.
```