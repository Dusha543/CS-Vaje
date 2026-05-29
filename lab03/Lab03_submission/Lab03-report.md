## Analysis and Report

### Nmap Results

The Nmap scan identified one open TCP port:

| Port | Service | Version |
|--------|---------|---------|
| 22/tcp | SSH | OpenSSH 8.9p1 Ubuntu |

### Hydra Results

Hydra successfully performed a brute-force attack against the SSH service using a small password list I created.

Result:

```text
[22][ssh] host: 172.17.0.2 login: testuser password: test123
```

The attack successfully found the correct password (`test123`) for the user `testuser`.

### Why are weak passwords dangerous?

Weak passwords can be discovered quickly using automated tools such as Hydra. Attackers can test thousands or even millions of passwords until they find a valid combination and more common the password is the higher the chances of it being in the password list used for the attack.

### Why should unused ports be closed?

Open ports expose services to potential attackers. Each running service increases the attack surface of a system.

## Reflection and Analysis

### How would you protect the SSH server from brute-force attacks?

I would use strong passwords, disable password authentication where possible, enable public-key authentication, and implement rate-limiting mechanismžs.

### What additional measures (e.g. limits on the number of logins, use of public-private keys, firewall) would you recommend?

I would recommend using SSH key authentication, disabling root login, limiting the number of failed login attempts, configuring a firewall to restrict SSH access, changing the default SSH configuration where appropriate, and enabling intrusion detection and monitoring solutions.

### How does the result change if we use a very strong password?

A strong password significantly increases the time required for a brute-force attack. If the password is long, unique, and complex, it may not be present in common password lists, making dictionary attacks less effective. As password complexity increases, the time required to crack it.