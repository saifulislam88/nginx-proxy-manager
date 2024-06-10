## Nginx proxy manager install using bash script in Linux

**To install the Nginx Proxy Manager, follow these steps using the provided script:**

[Create the Script](https://github.com/saifulislam88/nginx-proxy-manager/tree/main?tab=readme-ov-file#1-create-the-script)

[Make the Script Executable](https://github.com/saifulislam88/nginx-proxy-manager/tree/main?tab=readme-ov-file#2make-the-script-executable)

[Run the Script](https://github.com/saifulislam88/nginx-proxy-manager/blob/main/README.md#3-run-the-script)

[Access Nginx Proxy Manager](https://github.com/saifulislam88/nginx-proxy-manager/blob/main/README.md#4-access-nginx-proxy-manager)


### **1. Create the Script:**

Save the following script as `nginx-proxy-manager-install.sh`:

     ```bash
     
     #!/bin/bash
   
     # Nginx Proxy Manager Install Script | Copyright 2024, Md. Saiful Islam(mSI)
     # SET IP
     private=$(ip route get 8.8.8.8 | sed -n '/src/{s/.*src *\([^ ]*\).*/\1/p;q}')
     behindnat=$(curl -s http://whatismyip.akamai.com/)
     echo "This command is designed to be run on a fresh system. If it is not, turn back and reinstall or redeploy this instance."
     clear
     echo "Updating aptitude cache......"; apt update
     clear
     echo "Installing Docker......"; apt install docker
     clear
     echo "Installing Docker Compose......"; sudo apt install docker-compose
     clear
     echo "Installing git client......"; apt install git
     clear
     echo "Cloning proxy directory......"; git clone https://github.com/saifulislam88/nginx-proxy-manager
     clear
     echo "Changing directory......"; cd nginx-proxy-manager
     clear
     echo "Starting Proxy......"; docker-compose up -d
     clear
     echo -e "\e[31mNginx Proxy Manager has successfully been installed.\e[0m";
     echo "To login, head to http://$private:81 and continue configuration";
     echo "The default credentials are:";
     echo "Username/Email: admin@example.com";
     echo "Password: changeme";
     echo "Change these as soon as possible.";
     echo "If this is a Public Cloud instance, the correct URL is: http://$behindnat:81"
     exit


### **2.Make the Script Executable:**

Open a terminal and navigate to the directory where the script is saved. Run the following command to make the script executable:

  chmod +x nginx-proxy-manager-install.sh

### **3. Run the Script:**

Execute the script to install Nginx Proxy Manager:

  sudo ./nginx-proxy-manager-install.sh


### **4. Access Nginx Proxy Manager:**

Once the installation is complete, access the Nginx Proxy Manager via your web browser:

 - **Local Access: http://<private_ip>:81**
 - **Public Cloud Access: http://<public_ip>:81**

    Default Login Credentials:
    
    Username/Email: admin@example.com
    Password: changeme

**Important: Change the default credentials as soon as possible for security reasons. By following these steps, you will have successfully installed Nginx Proxy Manager on your system.**
