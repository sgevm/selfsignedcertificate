# selfsignedcertificate
```
How to Create a Self-signed Client Certificate with OpenSSL

openssl download: https://code.google.com/archive/p/openssl-for-windows/downloads


https://mcilis.medium.com/how-to-create-a-self-signed-client-certificate-with-openssl-c4af9ac03e99
https://www.makethenmakeinstall.com/2014/05/ssl-client-authentication-step-by-step/


1. use windows powershell

2.	run 
	$env:RANDFILE=".rnd"
	
3.
First, we need to create a Root CA certificate which will be used for creating the Server and Client certificates.

To make it simple, I’ve added the passwords to the commands (with the value “changeme”)!
>> openssl genrsa -aes256 -passout pass:crazyadmin -out ca.pass.key 4096



This command creates an encrypted RSA private key for CA Root.
>> openssl rsa -passin pass:crazyadmin -in ca.pass.key -out ca.key



This command extracts RSA private key.
openssl req -new -x509 -days 1095 -key ca.key -out ca.crt



This command creates the root certificate with the key. 
For this request, I supplied some dummy information for the fields Country Name, 
State or Province Name, 
Locality Name (eg, city) [Default City], 
Organization Name (eg, company) [Default Company Ltd], 
Organizational Unit Name (eg, section), 
Email Address.

For the Common Name (eg, your name or your server’s hostname) field we should specify a distinguishable name (like “TestRootCA”).


Second, we can use this CA certificate to create a server certificate that can be used for the SSL connection:
>> openssl genrsa -aes256 -passout pass:crazyadmin -out server.pass.key 4096



This command creates an encrypted RSA private key for Server.
>> openssl rsa -passin pass:crazyadmin -in server.pass.key -out server.key


This command extracts RSA private key.
>> openssl req -new -key server.key -out server.csr

crazycat
```

