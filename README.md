# freshly
Freshly VM Vulnhub Walkthrough


## netdiscover

Obtain the IP of the VM. The target is 192.168.56.101.

![Alt text](./netdiscover.png?raw=true)


## nmap

An nmap scan identified the following services.

![Alt text](./nmap.png?raw=true)


## nikto

A nikto scan was run on all ports. The 'login.php' page was identified as vulnerable.

![Alt text](./nikto.png?raw=true)

A standard query to the login form yields a '0' displayed.

![Alt text](./sqli_noinject.png?raw=true)

A query with an injection test in the parameter displays a '1'.

![Alt text](./sqli_inject.png?raw=true)


## sqlmap

Sqlmap is used to test for a vulnerability and enumerate the backend.

A POST query is crafted for testing.

![Alt text](./sqlmap1.png?raw=true)

Sqlmap IDs the vulnerable parameter.

![Alt text](./sqlmap_vuln.png?raw=true)

A query is crafted for further enumeration.

![Alt text](./sqlmap_enumdb.png?raw=true)

The databases are IDed.

![Alt text](./dbs.png?raw=true)

The credentials in the table are displayed.

![Alt text](./creds.png?raw=true)


## browser

The compromised credentials are valid for the Wordpress login.

A plugin to execute PHP code is added and the code modified for our environment.
![Alt text](./add_plugin.png?raw=true)
![Alt text](./shellcode.png?raw=true)


## low priv shell

Executing the widget by visiting the home page results in a low-priv shell returned to our netcat listener.

![Alt text](./low-shell.png?raw=true)


## root

<pre>
\(*_*)
  ( (>
  /  \
</pre>

Using the 'su' command to attempt a quick privilege escalation is successful with the compromised password.

![Alt text](./root.png?raw=true)


## ctf

The notes for this challenge elude to a secret in a sensitive file. We see the expression 'SECRET =' in '/etc/shadow' and '/etc/passwd', both of which are sensitive files. This may or may not be the end of the challenge.

![Alt text](./ctf.png?raw=true)


## post

Post exploitation results in a successful crack of one of users passwords on the Freshly VM. More may be crackable, I did not let the rockyou run complete.

![Alt text](./crack.png?raw=true)


## thanks

Thanks out to TopHatSec for the VM challenge.
