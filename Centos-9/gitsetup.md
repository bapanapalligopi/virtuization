To install Git on CentOS Stream 9, follow these steps:

### **Step 1: Update System Packages**
Ensure that your system's packages are up to date:
```bash
sudo dnf update -y
```

### **Step 2: Install Git**
You can install Git using the `dnf` package manager. Git is available in the default CentOS repositories.

1. Install Git:
   ```bash
   sudo dnf install git -y
   ```

### **Step 3: Verify Git Installation**
After the installation is complete, verify the version of Git installed by running:
```bash
git --version
```
You should see the version of Git installed, like this:
```
git version 2.x.x
```

### **Step 4: Configure Git (Optional but Recommended)**
Once Git is installed, it's recommended to configure your user details for Git:

1. Set your name:
   ```bash
   git config --global user.name "Your Name"
   ```

2. Set your email:
   ```bash
   git config --global user.email "youremail@example.com"
   ```

### **Step 5: Verify Git Configuration (Optional)**
Check the configuration to make sure it was set correctly:
```bash
git config --global --list
```

This will display the configured details, like:
```
user.name=Your Name
user.email=youremail@example.com
```

### **Git Installation Complete!**
You have successfully installed and configured Git on CentOS Stream 9. You can now start using Git to manage your code repositories.
