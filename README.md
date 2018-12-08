# Self Certificate Generator

Provide simple way to generate a CA and server certificates for development purposes.

Examples :

`self-certificate-generator --gen-ca --server-domains=example.com` generates a CA (ca.cert.pem, ca.key.pem) + server certificate for example.com (server.cert.pem, server.key.pem)

`self-certificate-generator --server-cert=./example.cert.pem --server-key=./example.key.pem --server-domains=example.com` generates a server certificate for example.com and sign it with the default CA (ca.cert.pem, ca.key.pem). If `./example.cert.pem` exists, use its serial and adds 1. 

`CA_KEY_PASSWORD=mypassword self-certificate-generator --ca-cert=./my-ca.cert.pem --ca-key=./my-ca.key.pem --server-cert=./example.cert.pem --server-key=./example.key.pem --server-cert-serial=150 --server-domains="example.com,*.example.com,*.test.example.com"` a full example that generates a new server certificate for example.com and sub-domains. Use `CA_KEY_PASSWORD` for decrypting the `my-ca.key.pem` to sign the server certificate. Finally, sets its serial to 150 to prevent browser rejection (by default sets to 1 or increment from previous certificate).
