Solidous Management Projects
==================================================================

Install Solidous Projects - Ubuntu 14.04
------------------------------------------------------------------

`` sudo adduser solidous sudo``  
``sudo apt-get install tomcat7``  
``sudo apt-get install mysql-server`` (root/root)  
``mysqladmin -u root -proot create solidous``  
``sudo rm -r /var/lib/tomcat7/webapps/ROOT``  
``sudo cp solidous.war /var/lib/tomcat7/webapps/ROOT.war``  
``mkdir /home/solidous/documents``  
``chown tomcat7 /home/solidous/documents``  

Fix Heap Size(Example for a server with 512M physical memory 512M)
------------------------------------------------------------------
``echo CATALINA_OPTS="-Xms256m -Xmx256m -XX:MaxPermSize=256m" > /usr/share/tomcat7/bin/setenv.sh``  

To run on port 80.
------------------------------------------------------------------

###By default tomcat run on port 8080.  
For 1G physical memory change 256 to 512 or 768 max.*  
Change port 8080 to 80 in /etc/tomcat7/server.xml  
``<Connector port="80" protocol="HTTP/1.1" connectionTimeout="20000" URIEncoding="UTF-8" redirectPort="443" />``  

###Install Authbind  
``apt-get install authbind``  

First, set ``AUTHBIND=yes`` in ``/etc/default/tomcat7`` file  
``sudo touch /etc/authbind/byport/80``  
``sudo chmod 500 /etc/authbind/byport/80``  
``sudo chown tomcat7 /etc/authbind/byport/80``  
