# 🔐 How to Create an SSH Key-Pair

## 1. Create a Key Pair

### Using the Amazon EC2 Console
- Go to AWS **EC2 Console** → select **Key Pairs** → select **Create Key Pair**
- Choose:
  - Key type: **RSA**
  - File format: **.pem**

⸻

## 2. Set File Permissions on Your Private Key

Change directory to where you saved this new private key using `cd` (cd = change directory)

Regardless of how the key was created, ensure it’s not publicly viewable by running (remember to replace `<your-key.pem>` with your key name):

`chmod 400 <your-key.pem>` (chmod = change permission mode)

This restricts file access so only you can read the private key.

⸻

## 3. Retrieve the Public Key from the Key Pair Material

📖 [AWS Documentation](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/describe-keys.html#retrieving-the-public-key)

To extract the public key from the .pem file, run:

`ssh-keygen -y -f /path_to_key_pair/my-key-pair.pem`

or:

`ssh-keygen -y -f /path_to_key_pair/my-key-pair.pem > /path_to_key_pair/my-key-pair.pub` 

- First command will print out public key directly for you to view
- Second command will not print out the public key, but save it into a seperate file in path `/path_to_key_pair/my-key-pair.pub`
- `-y`: Yield and retrive the public key from the key pair
- `-f`: Specifies the input filename

Copy and save the printed public key.

⸻

## 4. Troubleshooting: Private Key Permission Error

If you forget to change file permissions with `chmod 400`, you may see this error:

```bash
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
Permissions 0644 for 'julia.pem' are too open.
It is required that your private key files are NOT accessible by others.
This private key will be ignored.
Load key "julia.pem": bad permissions
```

To fix this, run:

`chmod 400 <your-key.pem>`
