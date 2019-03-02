## Generate a TLS certificate
```
cd ~/go/src/github.com/lu4p/genCert/
go build
./genCert --help
```
```
Usage of ./genCert:
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
./genCert --ca --ecdsa-curve P384 --host example.tld
```
This will result in ```key.pem``` and ```cert.pem```

## Generate TLS certificate for ToRat
```
cd ~/go/src/github.com/lu4p/genCert/
go run genCert.go --ca --host youronionadresshere.onion
cp *.pem ~/go/src/github.com/lu4p/ToRat_server
cat cert.pem
openssl x509 -pubkey -noout -in cert.pem
```
This will result in ```key.pem``` and ```cert.pem```
Then you need to change the cert in the serverCert var in ```~/go/src/github.com/lu4p/ToRat_client/client/netclient.go``` to the content of cert.pem.

The PublicKey belongs in ```~/go/src/github.com/lu4p/ToRat_client/crypto/key.go```
