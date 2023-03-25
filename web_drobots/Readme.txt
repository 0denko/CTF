For the challenge we're given a zip file containing source files of the docker container from which we need to get the flag.

Upon accessing the docker container we're prompted to enter username and a password.
Trying something like admin/admin we send a request to the server and get a 403 reply with "Invalid Credentials" prompt displayed on the page.

If we don't specify the password the same prompt is displayed but no request is sent to the server.

Let's examine the source code.

database.py file gives a clue saying that the code is vulnerable to SQL injection. Lets give that a try!

This is the line of code:
    user = query_db(f'SELECT password FROM users WHERE username = "{username}" AND password = "{password}" ', one=True)

We can try an injection: " OR 1=1 LIMIT 1 ;-- which will return any user bypassing a password verification
To make sure the request is sent to the server we need to enter something into a password field. Let's make it 1234

This will result in a following querry sent to the database:
    SELECT password FROM users WHERE username = "" OR 1=1 LIMIT 1
    
Using this we are able to login to the page and get the flag.

