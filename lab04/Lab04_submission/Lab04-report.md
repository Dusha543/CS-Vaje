## Commands Used

### Generat ingGPG key pair

```bash
gpg --full-generate-key
gpg --list-keys
```

### Creating a second id

```bash
gpg --full-generate-key
gpg --list-keys
```

### Creating the message

```bash
echo "To: difid@example.com
From: matic.dusa@example.com
Date: $(date)
Secret message: Confidential message" > message.txt
```

### Encrypt and sign the message

```bash
gpg --encrypt --sign --armor --recipient difid@example.com message.txt
```

### Decrypt and verify the signature

```bash
gpg --decrypt message.txt.asc > decrypted_message.txt
cat decrypted_message.txt
```

## Results

Two GPG key pairs were successfully generated. A message containing confidential information was created and encrypted for the recipient using the recipient's public key. At the same time, the message was digitally signed using the sender's private key.

The encrypted file was successfully decrypted and the digital signature was verified. GPG reported a valid signature.

## Reflection and Analysis

### 1. Difference between encryption and signing

Encryption is used to protect information so that only authorized recipients can read the content. Digital signing is used to verify the identity of the sender and to ensure that the content has not been modified during transmission.

### 2. Role of public and private key

The public key can be shared and is used for encryption and signature verification. The private key must remain secret and is used for decryption and creating digital signatures.

### 3. What happens when an encrypted file is modified?

If an encrypted or digitally signed file is modified, the integrity verification will fail. During decryption or signature verification, GPG will report that the signature is invalid or that the data has been altered.