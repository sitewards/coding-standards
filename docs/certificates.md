# Certificates

Generally speaking certificates should use the following values:

| Field              | Value                                |
|--------------------|--------------------------------------|
| Country Name       | DE                                   |
| State              | Hessen                               |
| Locality           | Frankfurt am Main                    |
| Organisation Name  | Sitewards GmbH                       |
| Organisational Unit| Engineering                          |
| Email Address      | `${YOUR_MAIL_ADDRESS}`               |

The only field that varies based on the certificate role is the "Common Name" field. This field is used in different
ways depending on the certificate, but only a single certificate matching those details can be created. Thus, the
common name should be created with the following conventions:

| Certificate Type | Common Name                            |
|------------------|----------------------------------------|
| Authority        | `ca.${TYPE}.${DOMAIN}.de`              |
| Server           | `${HOSTNAME_OF_SERVER}`                |
| Client           | `${LINUX_USER}@${HOSTNAME_OF_SERVER}`  |

Should the server not be addressable at the hostname address, please use the Subject Alternative Name (SAN) specification
of X509 to extend the validity of the certificate to multiple names.
