# Extracting the certificate and keys from a .pfx file

The .pfx file, which is in a PKCS#12 format, contains the SSL certificate (public keys) and the corresponding private keys. Sometimes, you might have to import the certificate and private keys separately in an unencrypted plain text format to use it on another system. This topic provides instructions on how to convert the .pfx file to .crt and .key files.

## Extract .crt and .key files from .pfx file
**Requirements:**  OpenSSL, obviously

1. Start OpenSSL from the OpenSSL\bin folder.
2. Open the command prompt and go to the folder that contains your .pfx file.
3. Run the following command to extract the private key:

```shell
openssl pkcs12 -in [yourfile.pfx] -nocerts -out [drlive.key]
```

You will be prompted to type the import password. Type the password that you used to protect your keypair when you created the .pfx file. You will be prompted again to provide a new password to protect the .key file that you are creating. Store the password to your key file in a secure place to avoid misuse.

4. Run the following command to extract the certificate:

```shell
openssl pkcs12 -in [yourfile.pfx] -clcerts -nokeys -out [drlive.crt]
```

5. Run the following command to decrypt the private key:

```shell
openssl rsa -in [drlive.key] -out [drlive-decrypted.key]
```

## Convert .pfx file to .pem format
There might be instances where you might have to convert the .pfx file into .pem format. Run the following command to convert it into PEM format.

```shell
openssl rsa -in [keyfile-encrypted.key] -outform PEM -out [keyfile-encrypted-pem.key]
```

## Evil-Winrm
Example useage with evil-winrm: 

```shell
evil-winrm -i [Target IP Address] -S -k
[keyfile-encrypted.key] -c [keyfile-encrypted-pem.key]
```
