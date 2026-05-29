## Reflection and Analysis

### 1. Why doesn't GPG detect MITM attacks automatically?

GPG verifies that a message was encrypted or signed using a specific key, but it cannot automatically determine whether the key actually belongs to the correct person.

### 2. What is a fingerprint and why is it important?

A fingerprint is a unique identifier of a public key. It allows users to verify that they have the correct key belonging to a specific person.

### 3. Why is email not a secure channel for exchanging keys?

Email messages can be intercepted, modified, or spoofed by attackers. If a public key is exchanged solely through email, an attacker may replace the legitimate key with a fake one. Without additional verification, the recipient may use / trust the wrong key.

### 4. How does the Web of Trust reduce the risk of MITM attacks?

The Web of Trust allows users to establish trust between echother by verifying and signing eachothers public keys. When multiple trusted individuals confirm a keys authenticity, it becomes more difficult for an attacker to successfully replace the key without it being detected.