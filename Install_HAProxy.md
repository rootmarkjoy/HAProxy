# HAProxy Setup:-

## Loadbalancer Server

#### Step 1: Install HAProxy on CentOS 7 Load Balancing Server:-

```sh
yum install haproxy
```
Once the installation finishes, start the HAProxy service with the following command:

```sh
systemctl start haproxy
systemctl enable haproxy
systemctl status haproxy
```

Now we will make sure we are allowing the HAProxy service to run through our firewall. The first command will enable the http server in the firewall.

```sh
firewall-cmd --permanent --zone=public --add-service=http
firewall-cmd --permanent --zone=public --add-service=https
```

Now, to make sure that the firewall rules are in effect, reload the firewall rules with the following command:

```sh
firewall-cmd --reload
firewall-cmd --list-all
```

#### Step 2: Install the Web Server on the Backend Servers:-

The other two servers would act as the backend servers. For this, we’ll set up Apache as the webserver to service requests that the HAProxy server would redirect.

We chose Apache because it’s perhaps the most widely used web server today. It is open source and has been a popular choice for setting up servers for web apps.


# Now on App servers 1 & 2, use the following commands to install Apache:


## App Server 1 & 2

```sh
# yum install httpd
```

Once the installation finishes, you’ll notice that the Apache service doesn’t start automatically. You need to enter the following command to start the service.

```sh
systemctl start httpd
systemctl enable httpd
```

Step 3: Configure Firewall Settings on Apache Servers

```sh
firewall-cmd --permanent --zone=public --add-service=http
firewall-cmd --permanent --zone=public --add-service=https
```

Now, to make sure that the firewall rules are in effect, reload the firewall rules with the following command:

```sh
firewall-cmd --reload
firewall-cmd --list-all
```
