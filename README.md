[![CircleCI](https://circleci.com/gh/lu4p/genCert.svg?style=svg)](https://circleci.com/gh/lu4p/genCert)
[![Go Report Card](https://goreportcard.com/badge/github.com/lu4p/genCert)](https://goreportcard.com/report/github.com/lu4p/genCert)
## Generate a TLS certificate
```
cd ~
go get -u -v github.com/lu4p/genCert
genCert --help
```
```
Usage of genCert:
  -ca
    	whether this cert should be its own Certificate Authority
  -duration duration
    	Duration that certificate is valid for (default 8760h0m0s)
  -ecdsa-curve string
    	ECDSA curve to use to generate a key. Valid values are P224, P256 (recommended), P384, P521
  -host string
    	Comma-separated hostnames and IPs to generate a certificate for
  -rsa-bits int
    	Size of RSA key to generate. Ignored if --ecdsa-curve is set (default 2048)
  -start-date string
    	Creation date formatted as Jan 1 15:04:05 2011
```
Example Certificate:
```
genCert --ca --ecdsa-curve P384 --host example.tld
```
This will result in the PrivateKey ```key.pem``` and the TLS-Certificate ```cert.pem```

Note: The PrivateKey should be kept PRIVATE, if the PrivateKey is disclosed an attacker is able to:
- imperson you 
- decrypt your traffic
- etc.