# 📘 Set Up Your JupyterHub

## Access the JupyterHub Interface

1. Open your **EC2 instance** on AWS.
2. Copy and open the **Public IPv4 address** in your browser.
3. Change `https://` to `http://` if needed, and log in as usual.
4. In JupyterHub:
   - Click `File` > `Hub Control Panel`
   - Click the `Admin` button
5. Click **"Add Users"**
   - Enter usernames, one per line
   - You can optionally enable users as **admin**
   - Example: enter `maria`
6. Click **Add Users**

---

## First Login as a New User

1. Open a **new browser window/tab**
2. Enter the same **Public IPv4 address**
3. Log in with the **new username** you just created (e.g., `maria`)
4. The first time the user logs in:
   - They will be prompted to **create a password**
   - This will become their permanent JupyterHub password

✅ Once signed in, the owner (you) will be able to:
- Monitor activity
- **Stop or restart their server** from the admin panel

---

# 📦 Install Packages in The Littlest JupyterHub (TLJH)

To install packages (like `pandas`) in your TLJH environment:

```bash
sudo -E pip install pandas
```

⚠️ Why `-E` is Important
- The `-E` flag tells sudo to preserve your environment variables, especially PATH.
- Without `-E`, pip might install the package to the root user’s Python environment instead of your active JupyterHub environment.

✅ Always use sudo `-E` when installing packages in TLJH to make sure they’re available in users’ notebooks.
