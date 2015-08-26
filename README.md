## FSND Project 5: Linux Server Config

This is not a copy & paste walkthrough. It still is full of spoilers.

1. The VM

Udacity will provide a virtual machine running in the Amazon cloud. The
IP address is given on your Udacity account page. The VM can be also be
managed (as in: created/started and deleted) from that page.

You will not find the page "Development Environment" in the "My Account"
menu on the left. The link is given in the project details for P5.

2. SSH

On your hidden development environment page you can also download the 
private ssh key to use for login as root to your Amazon instance. To use it,
download the private key, and move it to the .ssh directory in your home.
Make sure the file has the correct permissions, or ssh will refuse to
use it.

Google terms: 'ssh private key location', 'ssh permissions too open'
(These steps are also documented on the development environment page.)

3. Users
You will be asked later to disable direct logins for the root user for 
security reasons. If you do so, you need a different user to login with.
In this project, it is specified that this user should be called 'grader'.

Create this as a standard Linux user.

Google terms: 'ubuntu add user'

If you are bored, find out the difference between the 'adduser' and 'useradd'
commands.

4. Sudo

There are several ways to allow a user to execute commands with sudo. The
'ubuntu way' is using the /etc/sudoers.d/ directory. It is pretty
self-explanatory, but if in doubt:

Google terms: 'ubuntu sudoers.d'

In this step, make sure the 'grader' user can use sudo.

4a. SSH public key login for user 'grader'

This is only listed in the rubric, not in the project details.

You will be asked to disable root login by only allowing ssh login to 
non-root users. Also, ssh login should only be possible with ssh public keys, 
password authentication should be disabled. 

This is a very common security best practice: attackers know that every system 
has a user 'root' and will try to login with that account. Attackers do not 
know how you named your non-root users. If password login is enabled and no
further measures taken, an attacker can try to guess the password indefinitely
and may eventually get access that way.

Google terms: 'ssh key authentication'

You can either create a new key pair for the 'grader' user, or just use the
private key that has already been created and configured for the root user.

You will be asked to hand over the private key for that key pair when you
submit the project, so don't use a key pair that you actually use in real life.

Take care that the file permissions on all ssh-related files are set correctly
(it will complain). While you are playing around with SSH keys (and later,
configuration), make sure you ALWAYS stay logged in in at least one shell
window. Do NOT log out until you have successfully logged in with the new
configuration / user / key, or you might lock yourself out of the system.

5. Update all installed packages

Google terms 'ubuntu update packages'

Manual update is easy -- don't forget you need use sudo to do this, and
don't let the different options to apt-get confuse you.

In the rubric you'll find that for 'exceeds specifications' you need to
configure automatic unattended package updates. This is a bit controversial,
as every update also has a chance to break your system due to configuration
or setup changes you need to implement in your applications to run them on the
newer versions of your platform (web server, databases etc.).

It is, however, possible to only install security updates automatically. This
might be a good compromise depending on your needs. Security updates should be
installed as soon as possible, and the distributions (usually) don't include
dangerous changes / updates in security updates. You still should subscribe to
the security announcement channels of the distribution you are using, and of
course monitor the activity of any automatic updates you have set up.

Google terms 'ubuntu automatic security updates'


Addendum: sending / delivering local email

Some tasks ask for notification emails being sent in certain situations.

For this to work, you need a local MTA (mail transport agent) to be installed
that will accept and deliver the emails. The most popular alternatives on
linux systems are sendmail, exim4 and postfix, of which I _think_ postfix is
easiest to configure. The ubuntu package even contains a few default 
configurations, of which 'local-only' is sufficient for this project.

The choice of MTA is subjective, of course.

If you want to learn more about email systems and the abbreviations used
to describe them, google 'mta mua'. ('MUA' is the mail user agent, the mail
client an end user used for handling email.)

If you choose postfix, googling 'ubuntu postfix' will point you at the
official ubuntu manual section.
