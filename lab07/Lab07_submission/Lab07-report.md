## Task 1 – Script Inspection

### What does this script do?

The script simulates a simple software installation process. It displays an installation message, creates a directory named `src`, creates a script called `run.sh`, writes a command that prints `Hello`, moves the script into the `src` directory, and at the end executes it.

### Commands Used

```bash
cat install.sh
```

## Task 2 – Create SHA256 Checksum

### Commands Used

```bash
sha256sum install.sh > install.sh.sha256
cat install.sh.sha256
```

### Results

A SHA256 checksum was generated for the script and stored in a separate file. This checksum can later be used to verify that the script has not been modified.

## Task 3 – Verify Integrity

### Commands Used

```bash
sha256sum -c install.sh.sha256
```

### Results

The verification returned:

```text
install.sh: OK
```

This confirms that the file contents had not been modified.

## Task 4 – Sign the Checksum

### Commands Used

```bash
gpg --detach-sign install.sh.sha256
```

### Results

The checksum file was digitally signed using a GPG private key. This outputed a signature file (`install.sh.sha256.sig`) that can be used to verify the authenticity of the checksum.

## Task 5 – Verify the Signature

### Commands Used

```bash
gpg --verify install.sh.sha256.sig install.sh.sha256
```

### Results

GPG successfully verified the signature and reported a valid signature from the signing key.

## Task 6 – Simulate Tampering

### Commands Used

```bash
echo "echo MALICIOUS CODE EXECUTED" >> install.sh
sha256sum -c install.sh.sha256
```

### Results

After modifying the script, checksum verification failed because the file contents no longer matched the original checksum.

## Reflection and Analysis

### 1. Why should you never execute scripts without inspection?

Scripts may contain malicious commands that can modify files, install malware, steal data, or compromise the system. Reviewing the contents before execution helps identify potentially dangerous behavior before the script is run.

### 2. What does SHA256 guarantee?

SHA256 provides integrity verification. It allows users to detect whether a file has been modified since the checksum was created.

### 3. What does GPG guarantee?

GPG provides authenticity and integrity. It verifies that a file or checksum was signed by the owner of a specific private key and that the signed content has not been modified.

### 4. Can SHA256 prove the author of a file?

No. SHA256 only verifies file integrity.

### 5. Why is signing the checksum important?

Signing the checksum ensures that the checksum itself has not been modified by an attacker.

### 6. What happened after the script was modified?

After modifying the script, the calculated SHA256 checksum no longer matched the original checksum and the verification failed.