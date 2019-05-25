# Ansible Role: SSL Certificate
Generates self-signed SSL certificates.

## Requirements
None.

## Role Variables
Available variables are listed below, see `defaults/main.yml` for the default values.

```yaml
ssl_generate_full_chain_certificate: true
```
In addition to the certificate file, a full chain certificate (with a .pem extension) can be created by setting the `ssl_generate_full_chain_certificate` variable.

```yaml
ssl_certificates:
- common_name: example.test
- common_name: another-example.test
```
A list of certificates to generate. The `common_name` property is required and should be unique for each certificate.

```yaml
ssl_certificates:
- common_name: example.test
  country: GB
  state_province: Hertfordshire
  locality: St Albans
  organization: Your Company
```
 To override the default organizational properties used to configure a certificate, add any of the above attributes. The default properties are `GB` for `countryName`, `Hertfordshire` for `stateOrProvinceName`, `St Albans` for `localityName` and `Your Company` for `organizationName`.


 ```yaml
 ssl_certificates:
 - common_name: example.test
   email: admin@example.co.uk
   san_name: Subject Alternative Name
 ```
An optional email and subject alternative name can be added to the organizational properties using the `email` and `san_name` attributes.

```yaml
ssl_private_key_path: /etc/ssl/example.test
ssl_certificate_signing_request_path: /etc/ssl/example.test
ssl_certificate_path: /etc/ssl/example.test
```
To override the default paths used to generate the SSL certificates, set the 'path' variables as demonstrated above. The default paths are `/etc/ssl/private` for private keys, `/etc/ssl/csr` for certificate signing request files and `/etc/ssl/self-signed-certs` for the self-signed certificates.

```yaml
ssl_private_key_size: '4096'
```
To override the default number of bits (2048) used to generate the private key, set the `ssl_private_key_size` variable.

## Dependencies
None.

## Example Playbook
```yaml
- hosts: server
  become: yes

  tasks:
  - import_role:
      name: damianlewis.ssl
```
