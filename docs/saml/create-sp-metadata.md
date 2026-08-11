# How to generate SP metadata

## Install Shibboleth

If shibboleth is already installed and running, start at the configuration section below.

### Generate a repo file

```sh
sudo su -
cat << 'EOF' > /etc/yum.repos.d/shibboleth.repo
[shibboleth]
name=Shibboleth (rockylinux9)
# Please report any problems to https://shibboleth.atlassian.net/jira
type=rpm-md
mirrorlist=https://shibboleth.net/cgi-bin/mirrorlist.cgi/rockylinux9
gpgcheck=1
gpgkey=https://shibboleth.net/downloads/service-provider/RPMS/cantor.repomd.xml.key
enabled=1
EOF
```

```sh
yum install -y shibboleth
```

### Start the shibd service

```sh
sudo systemctl start shibd.service
sudo systemctl enable shibd.service
```

### Verify

```sh
sudo LD_LIBRARY_PATH=/opt/shibboleth/lib64 shibd -t
```

Its important that the last line of the output is:
>overall configuration is loadable, check console for non-fatal problems

## Configuration

### Generate Certificate and Key for SAML message signing/encrypting

The Shibboleth daemon (`shibd`) needs an X.509 keypair for signing and encrypting SAML messages. We recommend to use a dedicated self-signed certificate, independently configured from the SSL/TLS certificate used by the Web server. Checkout the [Certificate Overview](https://www.switch.ch/aai/certificates/) to better understand the role the certificates play in this context.

You can create an independent self-signed certificate with a lifetime of 10 years for usage by the Shibboleth SP only.

Generate the x509 certs with `keygen.sh` (Red Hat Enterprise, Rocky, CentOS):

```sh
sudo /etc/shibboleth/keygen.sh -f -u shibd -h <YOURHOST.EXAMPLE.ORG> -y 10 -o /etc/shibboleth/
```

### Generate the SP metadata

```sh
sudo /etc/shibboleth/metagen.sh -c /etc/shibboleth/sp-cert.pem -h YOURHOST.EXAMPLE.ORG > /etc/shibboleth/sp-metadata.xml
```

Check if these four attributes match with your app values

- entityID
- `AssertionConsumerService`
- <ds:X509Certificate>
- SingleLogoutService

This concludes the SP metadata generation.

> [!NOTE]
> You can open a ticket with ASKIT and ask them to register your SP in their IDP. Attach the metadata file at /etc/shibboleth/sp-metadata.xml that you generated in the ticket.
