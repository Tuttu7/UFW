 ### UFW ( uncomplicated firewall )
 
 
 #### Enabling / disabling ufw firewall service
 
 ```
 
root@ip-172-31-61-255:/home# ufw status
Status: inactive
root@ip-172-31-61-255:/home# ufw enable
Command may disrupt existing ssh connections. Proceed with operation (y|n)? y
Firewall is active and enabled on system startup
root@ip-172-31-61-255:/home# ufw status
Status: active
```

 #### Allow TCP packets on port 80:

```

root@ip-172-31-61-255:/home# ufw allow 80/tcp
Rule added
Rule added (v6)


root@ip-172-31-61-255:/home# ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere                  
80/tcp (v6)                ALLOW       Anywhere (v6) root@ip-172-31-61-255:/home# ufw deny 8080/tcp
Rule added
Rule added (v6)

```




 #### Deny tcp packets on port 8080
 
```
root@ip-172-31-61-255:/home# ufw delete deny 8080/tcp
Rule deleted
Rule deleted (v6)


root@ip-172-31-61-255:/home# ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere                  
8080/tcp                   DENY        Anywhere                  
80/tcp (v6)                ALLOW       Anywhere (v6)             
8080/tcp (v6)              DENY        Anywhere (v6) 

```

#### To allow both incoming and outgoing connections on port 22 for SSH

```

root@ip-172-31-61-255:/home# ufw allow ssh
Rule added
Rule added (v6)
root@ip-172-31-61-255:/home# ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere                  
22/tcp                     ALLOW       Anywhere                  
80/tcp (v6)                ALLOW       Anywhere (v6)             
22/tcp (v6)                ALLOW       Anywhere (v6)  
```

#### Allow specific IP address 

```

root@ip-172-31-61-255:/home# ufw allow from 192.168.1.7
Rule added
root@ip-172-31-61-255:/home# ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere                  
22/tcp                     ALLOW       Anywhere                  
Anywhere                   ALLOW       192.168.1.7               
80/tcp (v6)                ALLOW       Anywhere (v6)             
22/tcp (v6)                ALLOW       Anywhere (v6)
```

#### Deny an IP address 

```
root@ip-172-31-61-255:/home# ufw deny from 192.168.1.6
Rule added
root@ip-172-31-61-255:/home# ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     ALLOW       Anywhere                  
22/tcp                     ALLOW       Anywhere                  
Anywhere                   ALLOW       192.168.1.7               
Anywhere                   DENY        192.168.1.6               
80/tcp (v6)                ALLOW       Anywhere (v6)             
22/tcp (v6)                ALLOW       Anywhere (v6) 

```
