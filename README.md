# Micosoft Azure
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


===========================================================
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
