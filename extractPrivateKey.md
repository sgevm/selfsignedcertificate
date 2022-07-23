## https://security.stackexchange.com/questions/3779/how-can-i-export-my-private-key-from-a-java-keytool-keystore
## https://www.ssl.com/how-to/export-certificates-private-key-from-pkcs12-file-with-openssl/

```
--JKS to P12--
keytool -importkeystore -srckeystore 00D28000000HQBE.jks -destkeystore 00D28000000HQBE.p12 -deststoretype PKCS12 -srcstorepass 2022 -deststorepass jun2022


--Export certificate--
openssl pkcs12 -in 00D28000000HQBE.p12  -nokeys -out cert.pem


--Export unencrypted private key--
openssl pkcs12 -in 00D28000000HQBE.p12  -nodes -nocerts -out key.pem

```
