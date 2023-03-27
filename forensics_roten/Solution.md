For the challenge we're told the website admin is suspecting their site to being broken into and provides a packet capture for us to investigate.
Opening it in Wireshark we can see a large number of HTTP GET requests coming from IP 146.70.38.48. The requests seem to be looking for a file galacticmap.php and scanning throguh various directories.
Let's use "Find" and add galacticmap.php to the search string and then use Gind Previous. We'll see packet #18488 is a request at directory /uploads/ and the file was found there

Packet #18511 the IP 146.70.38.48 sends an HTTP GET request with a command included: /uploads/galacticmap.php?dir=%2Fvar%2Fwww%2Fhtml%2Fuploads&cmd=whoami HTTP/1.1 
The response says: Result of command execution: www-data

Seems the galacticmap.php is used to execute OS commands on the server. Let's see how it appeared there.

Packet #1929 shows that the file was uploaded from 146.70.38.48. If we right-click on the packet and select Follow -> HTTP Stream we'll see a long obfuscated PHP code (included in obfuscated.php)

The end of the code is eval function that executes content of the bhrTeZXazQ variable. We can use PHP Sandbox (1) to work with that code. We'll change the eval function to var_dump function that will display the content of bhrTeZXazQ

The content of the variable is the regular PHP code that contains the flag in the comments

(1) https://onlinephp.io/