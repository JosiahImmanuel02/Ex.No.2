# 19CS545-Ex2 - Configure SElinux in GitHub

# AIM:
To create a Repository

# Procedure:

1. Checking SELinux ports
The first command semanage port -l | grep http checks the Security-Enhanced Linux (SELinux)
policy for ports associated with the http service. SELinux is a security feature in Linux that restricts
what programs can access. The semanage port -l command lists all defined SELinux ports and the
grep http command filters the output to show only ports related to http.
The output shows several ports including 80 (standard web traffic), 8080, 8118, 8123 and a range
from 10001 to 10010.
2. Adding a new port
The second command semanage port -a http_port_t tcp 82 adds a new port
number (82) to the http_port_t port definition. This allows http traffic on port 82 in addition to
the standard ports.
3. Verifying the change
The third command semanage port -l | grep http again checks the http ports. The
output now shows port 82 included along with the previously listed ports.
4. Opening the firewall
The next command firewall-cmd --permanent --add-port=82/tcp opens port 82 in
the firewall. A firewall is a software program that controls traffic in and out of a computer. By
default, most firewalls block all incoming traffic and this command adds an exception to allow
traffic on port 82. The --permanent flag tells the firewall to make the change permanent across
reboots.
5. Reloading the firewall
The command firewall-cmd --reload reloads the firewall configuration to accept the
changes.
6. Installing the Apache web server
The next command dnf install httpd -y installs the Apache web server using the dnf
package manager. Apache is a popular open-source web server that can be used to host websites.
The -y flag tells dnf to assume yes to all prompts, which is useful for unattended installations.
7. Starting the Apache service
3
The command systemctl start httpd starts the Apache web server.
8. Enabling Apache at boot
The command systemctl enable httpd tells the system to start Apache automatically
whenever the system boots.
9. Restarting Apache
The command systemctl restart httpd restarts the Apache web server. This is useful if
there were any configuration changes made that require the service to be restarted.
10. Testing the web server
The final command curl http://127.0.0.1 uses the curl command to test the web server.
The curl command is a utility for transferring data from or to a server. In this case, it is used to
fetch the default web page from the web server running on the local machine (localhost -
127.0.0.1).
The successful output shows that the web server is up and running and listening on port 82 as
configured. 


# Output:

![Screenshot 2025-05-29 103248](https://github.com/user-attachments/assets/31359eac-64e6-4883-a0d7-930d49560e24)

![Screenshot 2025-05-29 103302](https://github.com/user-attachments/assets/b90c3b3d-0887-4a44-8c83-a7f1a050f6f3)


# Result:

Thus a Repository has been created successfully.
