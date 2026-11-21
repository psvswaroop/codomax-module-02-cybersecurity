# Lab 01 — Linux Security Fundamentals

## Aim
Review Linux files, permissions, ownership, users, groups and process inspection in a controlled local environment.

## Commands reference
```bash
pwd
ls -la
id
getent group
stat access.txt
chmod 640 access.txt
ps aux
```

For account/group administration in a disposable lab only:
```bash
sudo groupadd securityteam
sudo useradd -m cyberuser
sudo usermod -aG securityteam cyberuser
id cyberuser
```

## Expected interpretation
- `id` shows the current UID, primary GID and supplementary groups.
- `stat` displays ownership and permission metadata.
- Mode `640` means owner read/write, group read, others no access.
- `ps aux` lists running processes.

## Safety
Do not modify system accounts or permissions on important files. Use a disposable VM and test accounts. The commands above are a reference; this document does not claim they were executed during this submission.
