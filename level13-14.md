# Bandit Level 13 → 14

## Challenge
No password given this time.
Got a private SSH key instead.
Had to use the key to login as bandit14.

## What I Learned
SSH private key can be used instead of password.
Private key permissions MUST be 600.
Never connect to localhost on OverTheWire port 2220.

---

## FAILED ATTEMPTS

### Attempt 1 - Tried localhost (BLOCKED)
ssh -i sshkey.private bandit14@localhost -p 2220
ERROR: Connecting from localhost is blocked to conserve resources

### Attempt 2 - Wrong port (BLOCKED)
ssh -i sshkey.private bandit14@localhost
ERROR: Port 22 is not intended for OverTheWire

### Attempt 3 - File with space in name (FAILED)
nano private key
chmod +x ~/private key
ssh bandit14@bandit.labs.overthewire.org -p 2220 -i private key
ERROR: bash treated "key" as a separate command

### Attempt 4 - Wrong permissions (REJECTED)
chmod 0755 sshkey.private
ERROR: Permissions too open - SSH refused the key
WARNING: UNPROTECTED PRIVATE KEY FILE!

---

## SUCCESSFUL SOLUTION

### Step 1 - Read the private key on bandit13
cat sshkey.private
# Copy entire key output

### Step 2 - Save key on local machine
nano ~/sshkey.private
# Paste key and save

### Step 3 - Fix permissions (CRITICAL)
chmod 600 ~/sshkey.private
# 600 = only owner can read/write
# SSH will REJECT keys with open permissions

### Step 4 - Connect directly from local machine
ssh -i ~/sshkey.private bandit14@bandit.labs.overthewire.org -p 2220

### Step 5 - Get the password
cat /etc/bandit_pass/bandit14

---

## Key Rule
| Permission | Result |
|---|---|
| chmod 600 | SSH accepts key |
| chmod 755 | SSH rejects key |
| localhost | Connection blocked |
| overthewire.org | Connection works |

## Flag
MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS
