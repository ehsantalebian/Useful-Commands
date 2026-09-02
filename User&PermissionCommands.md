# User & Permission Commands

Here are some sets of User & Permission commands that can assist you in your day-to-day activities.

Add User to Privileged Groups

sudo usermod -aG sudo,docker [username]

Inspect User IDs, Groups, and Membership

id [username]
List Allowed Sudo Commands for Current User


sudo -l
Change File Ownership Recursively


sudo chown -R [user]:[group] /path/to/directory
Set Standard Directory and File Permissions


chmod 755 /path/to/script.sh
chmod -R 644 /path/to/files/