To install Java 17 on CentOS Stream 9, follow the steps below:

### **Step 1: Update System Packages**
First, update your system to make sure you have the latest packages and dependencies:
```bash
sudo dnf update -y
```

### **Step 2: Install OpenJDK 17 from the DNF Repositories**
CentOS Stream 9 provides OpenJDK 17 in the default repository, so you can easily install it using `dnf`.

Run the following command to install OpenJDK 17:
```bash
sudo dnf install java-17-openjdk-devel -y
```

This command will install the JDK (Development Kit) version of Java 17, which is necessary for development purposes. If you only need the JRE (Java Runtime Environment) version, you can install `java-17-openjdk` instead.

### **Step 3: Verify the Installation**
After installation, verify that Java 17 has been successfully installed by checking the version:
```bash
java -version
```
You should see output like this:
```
openjdk version "17.0.1" 2021-10-19
OpenJDK Runtime Environment (build 17.0.1+12-39)
OpenJDK 64-Bit Server VM (build 17.0.1+12-39, mixed mode, sharing)
```

### **Step 4: Set Java 17 as the Default Java Version**
If you have multiple Java versions installed and want to set Java 17 as the default version, run the following command:
```bash
sudo alternatives --config java
```

This will display a list of installed Java versions. Select the number corresponding to Java 17 and press Enter.

### **Step 5: Set JAVA_HOME (Optional)**
You may want to set the `JAVA_HOME` environment variable to make it easier to work with Java. To do so, follow these steps:

1. Find the path of Java 17 installation:
   ```bash
   sudo update-alternatives --display java
   ```

   Look for the path in the output (e.g., `/usr/lib/jvm/java-17-openjdk-17.0.1.12-0.el9_0.x86_64`).

2. Edit the `.bash_profile` file:
   ```bash
   nano ~/.bash_profile
   ```

3. Add the following line at the end of the file (replace `<java_install_path>` with the actual path you found):
   ```bash
   export JAVA_HOME=<java_install_path>
   export PATH=$JAVA_HOME/bin:$PATH
   ```

   For example:
   ```bash
   export JAVA_HOME=/usr/lib/jvm/java-17-openjdk-17.0.1.12-0.el9_0.x86_64
   export PATH=$JAVA_HOME/bin:$PATH
   ```

4. Save the file and exit (`Ctrl + X`, then `Y`, and `Enter`).

5. Reload the profile:
   ```bash
   source ~/.bash_profile
   ```

### **Step 6: Verify JAVA_HOME**
Verify that the `JAVA_HOME` environment variable is correctly set:
```bash
echo $JAVA_HOME
```

It should return the path to your Java 17 installation (e.g., `/usr/lib/jvm/java-17-openjdk-17.0.1.12-0.el9_0.x86_64`).

### **Optional: Installing Oracle JDK 17**
If you prefer Oracle JDK instead of OpenJDK, you will need to download it manually from the Oracle website and follow the installation instructions.

1. Download the Oracle JDK 17 from [Oracle Downloads](https://www.oracle.com/java/technologies/javase-jdk17-downloads.html).
2. Extract the downloaded archive and move it to an appropriate directory (e.g., `/opt`).
3. Set the `JAVA_HOME` environment variable to point to the Oracle JDK directory.

Let me know if you encounter any issues during the installation process!
