# 👥 Adding New Users to Your EC2 Instance

📖 Reference: [AWS Knowledge Center – Add New Linux Users](https://repost.aws/knowledge-center/new-user-accounts-linux-instance)

---

## Add a New User

1. Act as a super user (advanced privillages) to add a new user:
```bash
sudo adduser new_user --disabled-password
```
Explanation:
- `sudo`: Superuser do — temporarily gives admin privileges.
- Replace new_user with your actual username.
- `--disabled-password`: Avoids using a password. This is important to ubuntu based systems, if you don’t add that, it will prompt you for a password when you add new user. For better security, we don't like using password, we prefer login via SSH keys only.

⸻

2. Switch to the new user:

```bash
sudo su - new_user
```

- Replace new_user with your actual username.

⸻

3. Create the .ssh directory in the new user’s home directory:

```bash
mkdir .ssh
```

4. Change permission setting for the .ssh directory:

```bash
chmod 700 .ssh
```

🔐 Only the new user can read/write/execute the .ssh directory.

- First digit (7) = 4 + 2 + 1 = read (4) + write(2) + execute (1) for owner of this file/folder

⸻

5. Create an empty authorized_keys file:

```bash
touch .ssh/authorized_keys
```

6. Add the user’s public key (e.g., this public key is sent to you from your new user):

```bash
nano .ssh/authorized_keys
```

or 

```bash
vi .ssh/authorized_keys
```

- Paste the public key retrieved from new user's .pem file into this file, now maria's public key is added into this authorized key file.
- if you use `vi`, you need to type `i` to start insert mode, after you paste the paste the public key into the file, press `esc` to escape, then type `:wq` to save and quit the file.
- ⚠️ **IMPORTANT NOTE** New user should only send their public key file or public key string to you, NOT their `.pem` file, their `.pem` file contains private key too, private key should never be shared with anyone else!!

⸻

7. Secure the authorized_keys file:

```bash
chmod 600 .ssh/authorized_keys
```

- 🔐 Ensures only the user can read/write the file.
- First digit (6) = 4 + 2 = read (4) + write(2) for owner of this file/folder

⸻

8. Exit back to the original user using `exit` command, you need to type `exit` twice to completely leave the current session of SSH:

```bash
exit
```

9. Now the new user can log in using their private key:

```bash
ssh -i my-key.pem new_user@<ec2-public-ip>
```

⸻


## 🗂️ Set Up a Common Shared Folder on EC2


Purpose:

Create a shared space where all users can access common files.

⸻

1. Change to the /home directory:

```bash
cd ~/home` or `cd ..
```

2. List all directories, sorted by time (oldest first), human-readable:

```bash
ls -ltrh
```

3. Create a shared directory using -p:

```bash
sudo mkdir -p /srv/data/my_shared_data_folder
```

- **Why use -p?**
    - Without -p, the command fails ("No such file or directory" error) if parent folders (e.g., "/srv/data") don’t exist.
    - With -p, it will:
        - Create `/srv` if missing
        - Create `/srv/data` if missing
        - Create `/srv/data/my_shared_data_folder` if missing
    - ✅ This ensures smooth directory creation regardless of structure.
