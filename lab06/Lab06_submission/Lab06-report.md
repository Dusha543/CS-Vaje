## Commands Used

### Creating secrets

```bash
echo "API_KEY=super-secret-key-123
DB_PASSWORD=VeryStrongPassword" > secrets.env
```

### Symmetric encryption

```bash
gpg -c secrets.env
rm secrets.env
```

### Decryption

```bash
gpg -d secrets.env.gpg
gpg secrets.env.gpg
```

### Loading secrets into the environment

```bash
source secrets.env
echo $API_KEY
echo $DB_PASSWORD

unset API_KEY
unset DB_PASSWORD
```

## Results

A file containing sensitive information was created and protected using GPG symmetric encryption. After encryption, the original plaintext file was removed, leaving only the encrypted file. The encrypted file was later successfully decrypted and the secrets were loaded into variables.

## Reflection and Analysis

### 1. Why don't secrets belong in the source code?

Secrets should not be stored directly in source code because repositories are often shared among multiple users and may become publicly accessible.

### 2. What is the difference between symmetric and asymmetric secret encryption?

Symmetric encryption uses a single shared password for both encryption and decryption. Asymmetric encryption uses a public key for encryption and a private key for decryption. Asymmetric encryption provides better key management and eliminates the need to share passwords between users.

### 3. What happens if we lose the private key?

If the private key is lost and no backup exists, encrypted data can no longer be decrypted.

### 4. How would you handle this in a larger enterprise?

In a larger enterprise, dedicated secrets management solutions such as HashiCorp Vault, AWS Secrets Manager, Azure Key Vault, or Mozilla SOPS are usualy used.