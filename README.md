# Micosoft Azure
![image](https://github.com/user-attachments/assets/dfa76fe6-40ef-41f1-96fc-3a63e6c2fe9e)

In this repo, I'm documenting the learnings of Azure Services.

-------------------
## Index:
1. Regions and Zones
2. VM
3. Availability
4. VMSS
5. Scaling
6. Managed Services: Iaas, Paas, Saas
7. Azure Web App
8. Container
9. ACI (Azure Container Instances)
10. Container Orchestration (AKS & Service Fabric)
11. Serverless (Azure Functions)
12. Shared Responsibility Model
13. Storage types, Azure Storage
----------- Storage ---------------
15. Azure Storage - Data Redundancy
16. Region Pairs
17. Azure files
18. Database
19. Networking: Virtual Network, Subnet, Load balncer, Azure front door, Application Gateway vs API Gateway, Content Delivery Network (CDN)
20. Azure Network Security: Firewall, Network Security Group (NSG), DDoS, Azure Private Link & Private Endpoints, Bastin Host
21. Organizing & Managing Azure Resources: Resource Hierarchy (Management Groups > Subscription > Resource Group > Resources)

=====================================================================================
## 1. VM
Azure Virtual Machine (VM) is an IaaS (Infrastructure as a Service) offering.
It lets you create a virtual computer in the cloud. Just like your laptop or server, but running inside Azure’s datacenters.

* You control the OS, software, and settings.
* Azure provides the physical hardware.

### Hands-on Time!
Let's create a VM

<img width="959" alt="VM create 1" src="https://github.com/user-attachments/assets/44de676f-3118-4553-bac4-f1a494df56f0" />
<img width="959" alt="VM create 4 VM created" src="https://github.com/user-attachments/assets/cc2eeb4c-c44e-4156-8efb-b466f1fcf026" />
<img width="959" alt="VM create 5" src="https://github.com/user-attachments/assets/27d7a079-9379-4546-ba3b-bf4672e7ffa5" />

## 2. VMSS (Virtual Machine Scale Sets)?
Virtual Machine Scale Sets (VMSS) let you automatically create and manage a group of identical virtual machines (VMs).

* They all run the same application.
* They scale out (add VMs) when demand is high.
* They scale in (remove VMs) when demand is low.
* Azure handles the scaling for you.

### Handson Time!
Let's create a VMSS with 2 identical VMs, configure **Nginx** on both VMs, 1 Load balancer and then check the accessibility of both VM and LB using curl command using **Cloud Shell**

<img width="959" alt="azure-vmss" src="https://github.com/user-attachments/assets/c6e26819-831f-4c5d-a3c8-0f2f2a2e4261" />

Check the VMs..

<img width="959" alt="azure-vmss-vm" src="https://github.com/user-attachments/assets/ae97da28-d079-4a7a-91fa-ee66f3665383" />

These VMs can be accessible using their Public IPs as fillowing.. VM1

<img width="959" alt="azure-vmss-vm1-nginx" src="https://github.com/user-attachments/assets/83ecd6e1-5ec2-4879-b5a8-882ac5291e34" />

VM2

<img width="959" alt="azure-vmss-vm2-nginx" src="https://github.com/user-attachments/assets/c2d108a8-ca9b-4b86-9440-71f1429fc03c" />

Load Balancer (lb)

<img width="959" alt="azure-vmss-lb" src="https://github.com/user-attachments/assets/4aee159c-1037-429b-90db-b5a24bbb16dd" />

Now we will use Cloud shell and hit the lb url using **curl** command and lb will redirect on the availabele VMs.

```
curl http://135.235.112.61
```

<img width="959" alt="azure-vmss-access-vm-curl" src="https://github.com/user-attachments/assets/08ce4542-3f36-45c8-9d49-9dd95a24e6da" />

## 3. Azure Web App

Azure Web App is part of Azure App Service. It lets you host websites and web applications without managing any servers!
* Azure takes care of the hardware, updates, scaling, and security.
* You just focus on your app (like your website, API, or backend).

<img width="959" alt="azure-web-app1" src="https://github.com/user-attachments/assets/7f91d5c4-1a5e-4e3e-974e-a884815333da" />

Hit the domain of Web App on browser, we can see the web app page as follow.

<img width="959" alt="azure-web-app2" src="https://github.com/user-attachments/assets/d2e654f1-e39c-49e3-956e-fcf063cdbafc" />

## 8. Container
*  Lets create a container using azure portal
   
   <img width="959" alt="azure-contaiiner create" src="https://github.com/user-attachments/assets/959e9665-6c47-4012-9c3e-4c8e53e149ad" />

* We have given the Public IP for container, now hit the domain name on browser. We'll get the Azure Container Instances page.
  ```
  containerlh24.atayd9hqd7h6bpdn.westindia.azurecontainer.io
  ```
  <img width="956" alt="azure-container 2" src="https://github.com/user-attachments/assets/352f6ef3-10b3-435c-bfbc-30788f982863" />

## 16. Region Pairs
Azure Region Pairs are two Azure regions that are linked together to:

* Provide high availability 🛡️
* Support disaster recovery 🔄
* Ensure data backup across a wide area 🌐

If one region has an outage (disaster, update), the paired region can take over.

-----------------------------
### 17. Azure Files
Azure Files is a cloud-based shared file system that you can access just like a network drive — but it lives in Azure.

* Fully managed by Azure
* Accessible from Windows, Linux, and macOS
* Access over SMB protocol (the same protocol you use for network drives at work)
  
#### Hands-on Time!
<img width="959" alt="azure-storage1" src="https://github.com/user-attachments/assets/3475b104-bcc0-4d40-837f-4b848fb16d70" />
<img width="959" alt="azure-storage2-filshare" src="https://github.com/user-attachments/assets/6339efe4-acc8-43b4-8f8d-0785a6efb157" />

<img width="959" alt="azure-storage3-fileshare" src="https://github.com/user-attachments/assets/b4f42862-8997-476e-9891-1b62fdc161f1" />


## 15. Storage

Let's create a Storage Account from the Azure portal

<img width="959" alt="azure-storage1" src="https://github.com/user-attachments/assets/34c80a10-4902-442f-93e7-6d8d94543db9" />

<img width="959" alt="azure-storage2-filshare" src="https://github.com/user-attachments/assets/5c478acf-8231-4c9c-8dbf-853f5e081e0a" />

Create a File share in this storage

<img width="959" alt="azure-storage3-fileshare" src="https://github.com/user-attachments/assets/b94bed66-9d94-481a-b885-36e1d5a13a46" />


-----------------------------
## Azure Front Door?
Azure Front Door is a global, scalable entry point for your web applications.

It helps to:

* Route user traffic smartly,
* Accelerate performance (make apps load faster),
* Protect against threats like DDoS attacks.

 Think of it as a smart doorman that directs users to the best and fastest version of your app.

## Snapshot
A Snapshot is a full backup of a VM's disk that you can use for backup, recovery, or creating new disks/VMs.
* It captures the exact state of your VM disk.
* You can restore your VM later using the snapshot if needed (like after a crash or accidental deletion).

## Disc Backup
* A full backup of one or more VM disks (automated).
* Regular, scheduled backups for long-term retention.
* Whole VM, including OS and data disks.

### Key Difference:
* Snapshot = Manual, one-time, disk-level.
* Disk Backup = Scheduled, full VM-level protection using Azure Backup service.

## Swap Memory
Swap memory is virtual memory used when your system's RAM is full.
It's a portion of disk storage that acts like "extra RAM" to keep the system running smoothly.
System moves less-used data to swap space (on disk) to free up memory.
* It’s slower than RAM
* Helps prevent crashes when RAM is overloaded

## Server Hardening
* Server hardening means securing your server by reducing its vulnerabilities.
* Server hardening in Azure means following best practices to secure virtual machines, including limiting access, keeping systems updated, and monitoring activity.
* In Azure: Use tools like NSGs, Just-in-Time VM access, Microsoft Defender for Cloud

## 21. 
Management Group
<img width="959" alt="image" src="https://github.com/user-attachments/assets/9ec15943-0e9d-4a0b-8a04-0bf392deead9" />

We can see the current subscription details, as follow
<img width="959" alt="image" src="https://github.com/user-attachments/assets/69bf4e81-5498-4965-bb84-0c8a1db67ff8" />


