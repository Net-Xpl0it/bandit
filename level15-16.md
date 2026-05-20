# Bandit Level 15 → 16

## Commands
echo "8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo" | openssl s_client -connect localhost:30001 -quiet

## What I Learned
nc sends plain text - no encryption
openssl s_client sends data through SSL/TLS encryption
-quiet hides SSL handshake details
self-signed certificate warning is normal on CTF servers

## Difference
nc localhost 30000      = no encryption (level 14)
openssl s_client 30001  = SSL encrypted (level 15)

## Flag
kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx
