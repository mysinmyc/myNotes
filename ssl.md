SSL
===


[From baeldung](https://www.baeldung.com/openssl-self-signed-cert)

## Create self signed CA


Create CA key and self signed  certificate

`openssl req -x509 -sha256 -days 1825 -newkey rsa:2048 -keyout rootCA.key -out rootCA.crt`


## Create and sign domain certificate


- Create the private key and csr (-nodes means key not encrypted)

`openssl req -newkey rsa:2048 -nodes -keyout domain.key -out domain.csr`


- Create extended attributes file
```
authorityKeyIdentifier=keyid,issuer
basicConstraints=CA:FALSE
subjectAltName = @alt_names
[alt_names]
DNS.1 = domain
```

- Create signed certificate

`openssl x509 -req -CA rootCA.crt -CAkey rootCA.key -in domain.csr -out domain.crt -days 365 -CAcreateserial -extfile domain.ext`




## UBUNTU: add trusted ca

- copy CA certificate under `/usr/local/share/ca-certificates/`

- run  command `update-ca-certificates`


## RHEL: add trusted ca

- copy CA certificate under `/etc/pki/ca-trust/source/anchors/`

- run  command `update-ca-trust extract`