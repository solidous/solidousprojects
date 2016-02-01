Solidous Management Projects
==================================================================

Requeriments
------------------------------------------------------------------
>RAM: 512M or more  
Disk: 5GB or more  
Ubuntu 14.04, Tomcat 7 and Mysql (tested on)  

Install Solidous Projects
------------------------------------------------------------------
Get solidous from <http://solidous.org/files/solidous.war> and put these file in your server, login into the console.  
``sudo adduser solidous sudo``  
``sudo apt-get install tomcat7``  
``sudo apt-get install mysql-server`` (use default user and password: root/root)  
``mysqladmin -u root -proot create solidous``  
``sudo rm -r /var/lib/tomcat7/webapps/ROOT``  
``sudo cp solidous.war /var/lib/tomcat7/webapps/ROOT.war``  
``mkdir /home/solidous/documents``  
``chown tomcat7 /home/solidous/documents``  

Fix Heap Size
------------------------------------------------------------------
For a server with 512M physical memory  
``echo CATALINA_OPTS="-Xms256m -Xmx256m -XX:MaxPermSize=256m" > /usr/share/tomcat7/bin/setenv.sh``  
For 1G physical memory change 256 to 512 or 768 max.  

To run on port 80.
------------------------------------------------------------------

###By default tomcat run on port 8080.  
Change port 8080 to 80 in /etc/tomcat7/server.xml  
``<Connector port="80" protocol="HTTP/1.1" connectionTimeout="20000" URIEncoding="UTF-8" redirectPort="443" />``  

###Install Authbind  
``apt-get install authbind``  

Set ``AUTHBIND=yes`` in ``/etc/default/tomcat7`` file, and then  
``sudo touch /etc/authbind/byport/80``  
``sudo chmod 500 /etc/authbind/byport/80``  
``sudo chown tomcat7 /etc/authbind/byport/80``  

Accounts
----------------------------------------------------------------------
>*Application admin:*   
user: appAddmin  
password: a  

>*User:*  
user: demo  
password: demo  
