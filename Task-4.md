
# **Task 4: Enforce Security Best Practices in Your Git Repository**

## **1. Set Up User Access Controls**

### **For GitHub:**
1. Go to the repository **Settings** on GitHub.
2. Navigate to **Settings > Collaborators and Teams**.
3. Add team members and assign roles (**Admin, Write, Read**).
4. Use **GitHub Teams** to organize permissions at the team level if applicable.

![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/P%201.png)

![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/P%202.png)

### **For Git on Your Local Server:**
- Use tools like `gitolite` or `Gerrit` to enforce user access controls.
- Configure `~/.ssh/authorized_keys` for specific users with limited permissions.

---

## **2. Enable and Manage SSH Keys**

### **Generate SSH keys for secure authentication:**
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/G%201.png)

### **Add the SSH key to the user’s GitHub account:**
1. Copy the public key:
   ```bash
   cat ~/.ssh/id_rsa.pub
   ```
2. Add the key on GitHub:
   - Go to **Settings > SSH and GPG Keys > New SSH Key**.

![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/G%202.png)
### **Enforce SSH-only connections for Git operations:**
- Disable HTTPS password authentication and allow SSH.

---

## **3. Enforce Branch Protection Rules**

### **For GitHub:**
1. Go to **Settings > Branches > Branch Protection Rules**.
2. Click **Add Rule** and select the branch you want to protect (e.g., `main`).
![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/G%203.png)
3. Enable the following rules:
   - Require **pull request reviews** before merging.
   - Require **status checks** to pass before merging.
   - Require **signed commits**.
   - Restrict **who can push** to the branch.
![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/G%204.png)
### **For Git on Your Local Server:**
- Use hooks like `pre-receive` or `update` to restrict actions on specific branches.

---

## **4. Require Signed Commits**

### **Generate a GPG key:**
```bash
gpg --full-generate-key
```
![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/G%205.png)

### **Add the GPG key to GitHub:**
1. Export your GPG key:
   ```bash
   gpg --armor --export <your_email@example.com>
   ```
2. Add the exported key on GitHub under **Settings > SSH and GPG Keys > New GPG Key**.
![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/G%206.png)

![my image](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/G%207.png)


### **Configure Git to sign commits:**
```bash
git config --global user.signingkey <your_key_id>
git config --global commit.gpgsign true
```

### **Verify commit signing:**
```bash
git log --show-signature
```
![my images](https://github.com/jayymeg/project-3/blob/07bfae7ad74ef5fbf9f5bffd7b4f21ba61603832/T-4%20images/G%208.png)

---

## **5. Implement Auditing Mechanism**

### **GitHub:**
- Use the **Audit Log** available in **GitHub Organizations** to monitor activity.
- Go to **Settings > Audit Log** to track changes.

### **On Your Local Git Server:**
- Use server-side hooks (`post-receive` or `update`) to log changes and track who made commits.

---
