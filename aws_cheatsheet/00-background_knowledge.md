# Background Knowledge

## 1. SSH (Secure Shell)
SSH allows you to securely access a remote computer.  
- The **remote computer** is called the **server**.  
- The **computer you are using to connect** (your laptop or desktop) to this remote computer is the **client**.

---

## 2. Public Key & Private Key

These are used for secure communication via encryption & decryption:

- 🔐 **Public key** is like a **lock** you can share with others freely. Public key can encrypt a message.
- 🔑 **Private key** is the **key** that can open that lock — keep it secure and secret! Private key can decrypt the message encrypted by the public key.

Public keys can be shared freely; private keys should be stored safely and securely.

<img src="images/key_pair.png" alt="Ollie at the terminal" width="500"/>

---

## 3. AWS Lab Setup
We covered how to set this up in class:  
👉 [AWS Lab Setup and Login Instructions](https://pages.github.ubc.ca/MDS-2024-25/DSCI_525_web-cloud-comp_students/lectures/lecture3.html#aws-lab-setup)

---

## 4. Interacting with AWS

There are multiple ways to interact with AWS:

1. 🌐 Web interface  
2. 💻 Command Line Interface (CLI)  
3. 🐍 SDK (e.g., using Python)

Read more here:  
👉 [Ways to Interact with AWS](https://pages.github.ubc.ca/MDS-2024-25/DSCI_525_web-cloud-comp_students/lectures/lecture3.html#ways-to-interact-with-aws)

To set up the CLI on your local machine, follow this guide:  
👉 [AWS CLI Setup Guide](https://docs.aws.amazon.com/cli/latest/userguide/getting-started-install.html)