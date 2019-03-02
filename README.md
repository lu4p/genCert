### Generate TLS certificate
```
cd ~/go/src/github.com/lu4p/genCert/
go run genCert.go --ca --host youronionadresshere.onion
cp *.pem ~/go/src/github.com/lu4p/ToRat_server
cat cert.pem
openssl x509 -pubkey -noout -in cert.pem
```
This will result in key.pem and cert.pem.
Then you need to change the cert in the serverCert var in ```~/go/src/github.com/lu4p/ToRat_client/client/netclient.go``` to the content of cert.pem.

The PublicKey belongs in ```~/go/src/github.com/lu4p/ToRat_client/crypto/key.go```
