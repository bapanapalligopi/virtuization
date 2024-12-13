To install MySQL on CentOS Stream 9, follow these steps:

---

### **Step 1: Enable MySQL Yum Repository**
MySQL is not available in the default CentOS repositories, so you need to add the official MySQL repository.

1. Download the MySQL Yum repository package:
   ```bash
   sudo dnf install https://dev.mysql.com/get/mysql80-community-release-el9-1.noarch.rpm -y
   ```

2. Verify that the MySQL repository is enabled:
   ```bash
   sudo dnf repolist enabled | grep mysql
   ```

---

### **Step 2: Install MySQL Server**
1. Install the MySQL server package:
   ```bash
   sudo dnf install mysql-community-server -y
   ```

2. Verify the MySQL installation:
   ```bash
   mysql --version
   ```

---

### **Step 3: Start and Enable MySQL Service**
1. Start the MySQL service:
   ```bash
   sudo systemctl start mysqld
   ```

2. Enable the MySQL service to start on boot:
   ```bash
   sudo systemctl enable mysqld
   ```

3. Check the status of the MySQL service:
   ```bash
   sudo systemctl status mysqld
   ```

---

### **Step 4: Secure MySQL Installation**
MySQL comes with a security script to help configure basic security settings.

1. Retrieve the temporary root password:
   ```bash
   sudo grep 'temporary password' /var/log/mysqld.log
   ```
   Note down the password displayed in the output.

2. Run the security script:
   ```bash
   sudo mysql_secure_installation
   ```
   During the process:
   - Enter the temporary root password.
   - Set a new root password.
   - Answer "Yes" (Y) to all security prompts to remove test databases, disable anonymous users, and disallow root login remotely.

---

### **Step 5: Connect to MySQL**
1. Log in to MySQL using the root user:
   ```bash
   mysql -u root -p
   ```
   Enter the root password when prompted.

2. Verify the connection by running a command:
   ```sql
   SHOW DATABASES;
   ```

---

### **Optional: Allow Remote Connections (If Needed)**
1. Open the MySQL configuration file:
   ```bash
   sudo nano /etc/my.cnf
   ```
2. Look for the line:
   ```text
   bind-address = 127.0.0.1
   ```
   Change it to:
   ```text
   bind-address = 0.0.0.0
   ```
3. Restart MySQL:
   ```bash
   sudo systemctl restart mysqld
   ```

4. Configure the firewall to allow MySQL connections:
   ```bash
   sudo firewall-cmd --add-service=mysql --permanent
   sudo firewall-cmd --reload
   ```

---

### **MySQL Is Now Installed and Configured!**
You can now use MySQL to create and manage databases on CentOS Stream 9.
The error `GPG check FAILED` indicates that the GPG keys for verifying the downloaded MySQL packages are either missing or not properly installed. Follow these steps to resolve the issue and complete the installation:

---

### **Step 1: Import the GPG Key**
Manually import the GPG key for the MySQL repository:

```bash
sudo rpm --import /etc/pki/rpm-gpg/RPM-GPG-KEY-mysql-2022
```

---

### **Step 2: Retry the Installation**
Retry installing the `mysql-community-server` package:

```bash
sudo dnf install mysql-community-server -y
```

---

### **Step 3: If the Issue Persists**
If you still encounter the GPG error, disable the GPG check as a workaround (not recommended for production systems unless you fully trust the source):

```bash
sudo dnf install mysql-community-server --nogpgcheck -y
```

---

### **Step 4: Start MySQL Service**
After the installation is successful, start the MySQL server:

```bash
sudo systemctl start mysqld
sudo systemctl enable mysqld
```

---

### **Step 5: Verify MySQL Installation**
Check the installed MySQL version:

```bash
mysql --version
```

---

### **Step 6: Secure MySQL Installation**
Run the MySQL secure installation script to set the root password and configure security options:

```bash
sudo mysql_secure_installation
```

---

### **Additional Notes**
- Ensure your system has access to the MySQL GPG key from the repository.
- For production systems, it's critical to enable GPG checks to ensure package integrity and authenticity.
