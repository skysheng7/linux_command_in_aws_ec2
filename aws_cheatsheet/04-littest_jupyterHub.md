# 📘 Set Up Your JupyterHub

## Access the JupyterHub Interface and Add New User

1. Open your **EC2 instance** on AWS.
2. Copy and open the **Public IPv4 address** in your browser.
3. Change `https://` to `http://` if needed, and log in as usual.
   - ⚠️ Note: username is the <admin-user-name> you put into the code chunk under "Advanced details" when you first set up this EC2 instance
   - If this is the first time you open jupyterHub and try to login, this is your chance to setup the password, please remember this password because this will be the password for the rest of this project, you would need it every time you login again in the future.
4. In JupyterHub:
   - Click `File` > `hub control panel`
   - Click the `Admin` button
5. Click **"Add Users"**
   - Enter usernames, one per line
   - You can optionally enable users as **admin**
   - Example: enter `maria`

---

## First Login as a New User

1. Open a **new browser window/tab**, you can do Incognito mode
2. Enter the same **Public IPv4 address** as above
3. Log in with the **new username** you just created (e.g., `maria`)
4. The first time the user logs in:
   - They will be prompted to enter **password**, this is actually asking you to set a new password for the new user
   - This will become their permanent JupyterHub password
5. ✅ then you will be signed in as new user
6. Note: Owner (host) of this EC2 instance will be able to:
- Monitor activity
- **Stop or restart servers of other users** from the admin panel

---

# 📦 Install Packages in The Littlest JupyterHub (TLJH)

To install packages (like `pandas`) in your TLJH environment:

```bash
sudo -E pip install pandas
sudo -E pip install s3fs
sudo -E pip install pyarrow
```

- This will install these packages for all users, this is an universal install operation.
- ⚠️ Why `-E` is Important
    - The `-E` flag tells `sudo` (super user privillage) to preserve your current environment variables, especially PATH.
    - Without `-E`, pip might install the package using the root user’s environment variables (e.g., PATH to python), instead of your active JupyterHub environment's variables.
