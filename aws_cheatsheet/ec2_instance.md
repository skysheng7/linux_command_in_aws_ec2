# Set up EC2 Instance

## 🚀 Launching the Instance

1. Launch AWS lab, and start the lab on Canvas. Click the green-lit **AWS** button on Canvas, and you will be redirected to AWS web interface.
2. Search for **“EC2”** in the AWS Management Console.
3. Click **“Launch an instance”**.
4. Add a **name** (e.g., `sky-mds`).
5. Under **Application and OS Images (Amazon Machine Image)**:
   - Choose: **Ubuntu Server 22.04 LTS (HVM), SSD Volume Type - ami-XXXXXXXXXXXXXXXXX, leaving 64-bit (x86)**
   - 🔍 **Note**: An Amazon Machine Image (AMI) is not a Docker image.  
     - Docker image = lightweight, contains virtual environment to use a software or reproduce code
     - AMI = full virtual machine including OS and root filesystems

6. Under **Instance Type**, select: `t2.medium`:

    - This is the "hardware" setting of your virtual machine

7. Under **Key pair (login)**:
   - If it's your first time setting up this cluster: Click **“Create a new key pair”**, name it, key pair type = RSA, private key file format = pem, and **download the `.pem` file**.
   - Save the key-pair somewhere secure.
   - If setting up again: Choose the existing key pair you previously created.

8. Under **Network Settings**:
   - Select default Virtual Private Cloud (VPC) and subnet.

9. Under **Network Settings** → **Firwall (Security Groups)**:
   - Create or select a security group.
   - Ensure the following **rules** are checked:
     - ✅ Allow SSH traffic from Anywhere
     - ✅ Allow HTTPS traffic from the internet
     - ✅ Allow HTTP traffic from the internet

10. Under **Configure storage**:
    - Use root as storage with **30 GB** (recommended)
    - Select **General purpose SSD (gp2)** as volume type to reduce costs

11. Under **Advanced details**:
    - Add the following code chunk into the **"User data - optional"** section.
    - Replace `<admin-user-name>` with your **JupyterHub admin username** (e.g., `sky`).
    - ⚠️ **Note**: This username is for The Littlest JupyterHub inside of the EC2 instance — *not* your EC2 instance login.

    Example:
    ```bash
    #!/bin/bash
    curl -L https://tljh.jupyter.org/bootstrap.py \
        | sudo python3 - \
    --admin <admin-user-name>
    ```

12. click "launch instance"
13. After launching, search for your EC2 instance under **Instances** to monitor its status.
    - It might say “Running” before JupyterHub is fully set up — give it **15–20 minutes**.
    - You can also check **System Logs** during setup.

14. Click the **Connect** button on your instance page.
    - Choose the **SSH Client** tab
    - Follow the instructions to connect

---

## 🧑‍💻 Logging into EC2 Instance as Admin/Host

1. Open your **terminal**
2. Use `cd` to move to the directory where your private key (`.pem`) is saved
3. Run:
    ```bash
    chmod 400 sky-mds.pem
    ```

    ### 🔐 Why use `chmod 400`?

    - `chmod`: change file permissions
    - First digit (4): read permission for the owner
    - Second & third digits (0): no permissions for group or others

    ✅ Reasons to use `chmod 400`:
    - **SSH security**: Required by OpenSSH to avoid “permissions too open” error
    - **Protect against malware**: Restricts access to private key
    - **Avoid accidental modification**
    - **Safety on shared systems**

4. Connect using `ssh`:

    ```bash
    # Syntax
    ssh -i <path_to_private_key.pem> <username>@<ec2_hostname>

    # Example
    ssh -i ~/Downloads/sky-mds.pem ubuntu@ec2-54-555-555-555.compute-1.amazonaws.com
    ```

    - `-i` = identity file (your private key)
    - Default username for Ubuntu AMI is `ubuntu`

5. To log out of the instance, type:
    ```bash
    exit
    ```

---

## ⚠️ Important Notes About Billing

- Typing `exit` **does not stop AWS from charging you**
- You must click **“Stop Instance”** in the web interface to pause compute charges
- Stopping preserves your storage (still incurs storage cost)
- Clicking **“Terminate Instance”** deletes the instance permanently — no further charges