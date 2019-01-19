## Generate and Setup cryptographic keys
TorRAT uses a tls certificate to encrypt transport and a Rsa Keypair to save files encrypted to the clients disk.
The provided Keys are only for demonstration you will need to generate your own keys.

### Generate TLS certificate
```
cd ~/go/src/github.com/lu4p/genCert/
go run genCert.go --ca --ecdsa-curve P256 --host youronionadresshere.onion
cp *.pem ~/go/src/github.com/lu4p/ToRat_server
```
This will result in key.pem and cert.pem.
Then you need to change the cert in the serverCert var in ```~/go/src/github.com/lu4p/ToRat_client/client/netclient.go``` to the content of cert.pem.

### Generate Rsa Keypair
```
openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:4096
openssl rsa -pubout -in private_key.pem -out public_key.pem
```

This wil result in two files private_key.pem and public_key.pem you need to replace the provided keys with the newly generated ones.

The PrivateKey belongs in ```~/go/src/github.com/lu4p/ToRat_server/crypto/key.go```

The PublicKey belongs in ```~/go/src/github.com/lu4p/ToRat_client/crypto/key.go```
