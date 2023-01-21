
# SSH Port Forwarding

-   [Introduction](#introduction)
-   [Types of Port Forwarding](#types-of-port-forwarding)
    -   [Local Forwarding](#local-forwarding)
	     * [Demo Local Forwarding](#demo-local-forwarding)
    -   [Remote Forwarding](#remote-forwarding)
	     * [Demo reverse Forwarding](#demo-reverse-forwarding)
    -   [Dynamic Forwarding](#dynamic-forwarding)
	     * [Demo Dynamic forwarding](#demo-dynamic-forwarding)
-   [Comparison of Types](#comparison-of-types)
-   [Security Considerations](#security-considerations)
-   [Conclusion](#conclusion)
    -   [Recommendations and further reading](#recommendations-and-further-reading)
   

## Introduction

Secure Shell (SSH) is a protocol for securely connecting to remote servers. One of the most important features of SSH is the ability to forward ports, which allows for secure communication between a local machine and a remote server, even when the remote server is behind a firewall.

There are three types of port forwarding in SSH: local forwarding, remote forwarding, and dynamic forwarding. Each of these types serves a different purpose and can be used in different scenarios.

## Types of port forwarding:

## *Local Forwarding*

Local forwarding is used to forward a specific port on the local machine to a specific port on the remote server. This can be useful when a service on the remote server is not accessible from the local machine due to a firewall. The syntax for local forwarding is as follows:

`ssh -L local_port:remote_host:remote_port user@remote_server` 

For example, if you want to forward port 8080 on the local machine to port 80 on the remote server, you would run the following command:

`ssh -L 8080:remote_server:80 user@remote_server` 

### Use Cases

-   Accessing a web service running on a remote server that is not accessible from the local machine due to a firewall.
-   Connecting to a database server running on a remote machine and accessing it as if it were running on the local machine.
-   Bypassing a corporate firewall that blocks certain websites or services.
### Demo local forwarding

here is our example:  

![enter image description here](https://user-images.githubusercontent.com/75957098/213832060-a3ecff25-d3bb-4466-8a5b-4875e0685ed8.PNG)

## *Remote Forwarding*

Remote forwarding is used to forward a specific port on the remote server to a specific port on the local machine. This can be useful when a service on the local machine is not accessible from the remote server due to a firewall. The syntax for remote forwarding is as follows:

`ssh -R remote_port:local_host:local_port user@remote_server` 

For example, if you want to forward port 80 on the remote server to port 8080 on the local machine, you would run the following command:

`ssh -R 80:localhost:8080 user@remote_server` 

### Use Cases

-   Allowing remote users to access a service running on the local machine.
-   Setting up a reverse tunnel for remote server administration
-   Allowing a local development server to be accessed by a remote machine.
### Demo reverse forwarding  
  
  here is our example:  
  
![enter image description here](https://user-images.githubusercontent.com/75957098/213830877-a9372e34-cdbe-48e1-b692-cb458330526d.PNG)
## *Dynamic Forwarding*

Dynamic forwarding is used to forward all traffic sent to a specific port on the local machine to the remote server through an encrypted SSH tunnel. This can be useful when you want to use the remote server as a proxy for all network traffic. The syntax for dynamic forwarding is as follows:

`ssh -D local_port user@remote_server` 

For example, if you want to forward all traffic sent to port 1080 on the local machine to the remote server, you would run the following command:

`ssh -D 1080 user@remote_server` 

### Use Cases

-   Using the remote server as a proxy for all network traffic.
-   Accessing a local network resource from a remote server.
-   Bypassing internet censorship or geo-restrictions by using the remote server as a proxy.
### Demo dynamic forwarding

here is our example : 

![](https://user-images.githubusercontent.com/75957098/213830765-61eb5769-b98e-4fd1-b31c-ed456a783686.PNG)

## Comparison of types:  

When it comes to port forwarding, each type of forwarding serves a different purpose and can be used in different scenarios. Local forwarding is useful when you need to access a service on a remote server that is not directly accessible from your local machine. Remote forwarding is useful when you need to allow access to a service running on your local machine from a remote server. Dynamic forwarding is useful when you want to use the remote server as a proxy for all network traffic.

It's worth noting that all the above types of port forwarding can be used together in one ssh connection.

## Security Considerations

It is important to be aware of the security considerations when using SSH tunneling, as it can be exploited by hackers to gain access to your network. Here are some steps you can take to ensure the security of your SSH tunnel:

1.  Use strong passwords for all accounts that have access to the remote server.
    
2.  Use public key authentication instead of password authentication, if possible. This will prevent attackers from guessing your password and accessing your account.
    
3.  Limit the number of accounts that have access to the remote server, and carefully control who has access to the private keys needed for public key authentication.
    
4.  Use firewalls and other security measures to protect the remote server and your local network.
    
5.  Monitor the remote server and your local network for suspicious activity, and take appropriate action if any is detected.
    
6.  Keep all software and operating systems on the remote server and your local network up to date with the latest security patches.
    

By following these steps, you can help ensure the security of your SSH tunnel and protect your network from potential attacks.

## Conclusion

In conclusion, SSH port forwarding is a powerful feature that allows secure communication between a local machine and a remote server, even when the remote server is behind a firewall. There are three types of port forwarding in SSH: local forwarding, remote forwarding, and dynamic forwarding. Each of these types serves a different purpose and can be used in different scenarios. By understanding the differences and similarities between these types of port forwarding, you can use SSH more effectively to access remote resources and services.

### Recommendations and further reading

-   [SSH man page](http://manpages.ubuntu.com/manpages/saucy/man1/ssh.1.html)
-   [SSH Port Forwarding Tutorial](https://www.ssh.com/ssh/tunneling/example)
-   [Port Forwarding Explained](https://www.howtogeek.com/66214/how-to-forward-ports-on-your-router/)

