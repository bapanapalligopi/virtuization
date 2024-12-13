To install Maven on CentOS Stream 9, follow the steps below:

### **Step 1: Update the System**
First, make sure your system is up to date:
```bash
sudo dnf update -y
```

### **Step 2: Install Apache Maven using DNF**
CentOS Stream 9 provides Maven in the default repository, so you can install it using `dnf`. Run the following command:
```bash
sudo dnf install maven -y
```

### **Step 3: Verify Maven Installation**
After the installation is complete, verify that Maven is installed correctly by checking its version:
```bash
mvn -version
```

You should see output similar to the following:
```
Apache Maven 3.8.1 (cecedd343002696e1f2a8e6c2c8f9e1f4e3b1a3b; 2021-04-28T10:12:39-04:00)
Maven home: /usr/share/maven
Java version: 17.0.1, vendor: Oracle Corporation, runtime: /usr/lib/jvm/java-17-openjdk-17.0.1.12-0.el9_0.x86_64
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "5.14.0-70.13.1.el9_0.x86_64", arch: "amd64", family: "unix"
```

### **Step 4: Set the `M2_HOME` Environment Variable (Optional)**
If you need to set the `M2_HOME` environment variable to ensure that Maven is correctly recognized by all applications, follow these steps:

1. Open or create the `.bash_profile` file in your home directory:
   ```bash
   nano ~/.bash_profile
   ```

2. Add the following lines to set the `M2_HOME` and `PATH` variables:
   ```bash
   export M2_HOME=/usr/share/maven
   export PATH=$M2_HOME/bin:$PATH
   ```

3. Save the file and exit (`Ctrl + X`, then `Y`, and `Enter`).

4. Apply the changes by sourcing the `.bash_profile`:
   ```bash
   source ~/.bash_profile
   ```

### **Step 5: Verify Maven Again**
Finally, check if Maven is available and the environment variable has been set correctly:
```bash
mvn -version
```

You should see the version information of Maven, and the `M2_HOME` variable should point to the correct directory.

### **Optional: Installing a Specific Version of Maven**
If you need a specific version of Maven that is not available in the CentOS repository, you can download and install it manually.

1. Download the desired Maven version from the [Apache Maven Download page](https://maven.apache.org/download.cgi).
2. Extract the tar.gz file to a directory (e.g., `/opt/maven`):
   ```bash
   sudo tar -xvzf apache-maven-3.x.x-bin.tar.gz -C /opt
   ```
3. Set the `M2_HOME` environment variable to the extracted Maven directory and update your `PATH`:
   ```bash
   export M2_HOME=/opt/apache-maven-3.x.x
   export PATH=$M2_HOME/bin:$PATH
   ```
4. Add these lines to your `~/.bash_profile` to make them permanent.
   
After installation, Maven should be up and running on your CentOS Stream 9 system!
