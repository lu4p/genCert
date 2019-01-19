# Generate keys

The provided Keys are only for demonstration you will need to generate your own keys.

## Generate TLS certificate
```
go run genCert.go --ca --ecdsa-curve P256 --host youronionadresshere.onion
```

This wil result in two files key.pem an cert.pem you need to replace the provided certificates in the TorRAT_server with the newly generated ones.
Then you need to change the cert in TorRAT_client/client/netclient.go to the content of cert.pem.

## Generate Rsa Keypair
openssl genpkey -algorithm RSA -out private_key.pem -pkeyopt rsa_keygen_bits:4096

openssl rsa -pubout -in private_key.pem -out public_key.pem

This wil result in two files key.pem an cert.pem you need to replace the provided keys with the newly generated ones.

The PrivateKey belongs in TorRat_server/crypto/key.go

The PublicKey belongs in TorRat_client/crypto/key.go
