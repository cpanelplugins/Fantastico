Please ensure that the following are readily available on your server.

- cURL (for Internal PHP; both CGI and CLI versions)

You can test it as follows: `PHP -i | grep curl`

Expected Output: cURL Information => libcurl...

# How do I install Fantastico F3?

Please execute the following commands (as "root"; one after the other):

`mkdir --parents /var/netenberg/fantastico_f3
cd /var/netenberg/fantastico_f3 && curl -O https://licenses.netenberg.com/fantastico_f3/sources.tar.bz2
cd /var/netenberg/fantastico_f3 && tar --bzip2 --extract --file sources.tar.bz2`

Expected Output = None (unless you do not have a valid license in which case you will see a few "tar" errors)

`cd /var/netenberg/fantastico_f3/sources && $PHP index.php license`

Expected Output = XXX.XXX.XXX.XXX (your IP address): Pass

If you see Fail instead of Pass (inspite of having a valid license), please submit a ticket through your account.

`cd /var/netenberg/fantastico_f3/sources && $PHP index.php optimize`

This will do the following:
- registers the WHM component
- registers the cPanel component
- registers the "default" Features Set entry
- create appropriate symbolic links in all the cPanel themes
- rebuilds the cPanel sprites
- registers a new crontab entry (automatically keeps your copy up-to-date)

Expected Output = a lot of lines!

`cd /var/netenberg/fantastico_f3/sources && $PHP index.php scripts`
- This will register all the new scripts (more than 600)!
- Expected Output = XXXXXXXXXX (Script Name): OK
- (when the script in question is already up-to-date)
- Expected Output = XXXXXXXXXX (Script Name): Updated
- (when the script in question is updated)
- Expected Output = XXXXXXXXXX (Script Name): Not Updated
- (when the script in question is not updated)
At this point, your copy of Fantastico F3 is fully functional. You can visit the cPanel component and start installing scripts (visiting WHM component is not mandatory as was in F2).

Shortcut 1 (for cURL):

`curl https://licenses.netenberg.com/fantastico_f3/install.sh | /bin/bash`

Shortcut 2 (for wget):

`wget https://licenses.netenberg.com/fantastico_f3/install.sh -O - | /bin/bash`

# How do I update Fantastico F3?

Please execute the following commands (as "root"; one after the other):

`cd /var/netenberg/fantastico_f3/sources && $PHP index.php update`

This will update the core (if needed)

`cd /var/netenberg/fantastico_f3/sources && $PHP index.php scripts`

This will register all the new scripts (if any) and also update existing scripts (if needed)

Notes:
- The core and the scripts are independent and must be updated separately. You must execute both of the commands show above.
- This is only required if you do not have a crontab entry. A valid crontab entry will automatically execute both of the commands shown above at least once a day.

# How do I fix Fantastico F3?

Please execute the following commands (as "root"; one after the other):

`cd /var/netenberg/fantastico_f3/sources && $PHP index.php optimize`

Note: This is an all-encompassing command. It will traverse the entire breadth and depth of your copy of Fantastico F3 and fix any/all problems that it encounters. If this command does not solve your issue, please sign in to your netenberg account and open a new ticket.
