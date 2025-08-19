# QOL Setup
## setup git
``` shell
# Configure Git identity
git config --global user.name "Your Name"
git config --global user.email "your_email@example.com"

# Generate SSH key
ssh-keygen -t ed25519 -C "your_email@example.com"

# Start SSH agent and add key
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519

# Copy public key and add to GitHub
cat ~/.ssh/id_ed25519.pub
```
## openssh
https://documentation.ubuntu.com/server/how-to/security/openssh-server/index.html

```
sudo apt install openssh-server
sudo systemctl enable ssh
sudo systemctl start ssh
```