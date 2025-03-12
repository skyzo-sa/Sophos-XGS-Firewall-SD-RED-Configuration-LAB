# XG Firewall | SD-RED Configuration LAB

## Objective

The primary goal of this Sophos XGS-Firewall v21.0 SD-RED Configuration LAB is to configure and deploy Sophos SD-RED (Remote Ethernet Device) to securely extend a network to remote locations. This involves setting up secure site-to-site connectivity, optimizing traffic flow, and enforcing security policies between branch offices and the main corporate network.

### Job Skills Learned

- Deploying SD-RED devices to securely extend networks across remote locations.
- Configuring site-to-site VPNs or split-tunnel connections.
- Firewall Configuration & Management
-  VPN & Remote Access Security 
- Network Segmentation & Routing
- Cybersecurity & Compliance


### Tools Used

- Sophos XGS Firewall v21.0 device (or virtual instance) in virtualized environments (VMware).
- An SD-RED 20/60 device (or simulation setup)
- Access to the Sophos Central Management Portal
- SFOS 21.0 Web Interface (GUI)
- SFOS 21.0 Command Line Interface (CLI)
- Control Center Dashboard: Built-in monitoring tool for real-time traffic and event analysis.
- Backup and Restore Tools
- Traffic Generation Tools
- EVE-NG for simulating network devices (e.g., routers, PCs, or switches) to test


*Ref 1: Network Diagram*
![image](https://github.com/user-attachments/assets/96800c45-d57f-4ac9-a7d4-2c1ef0d26fea)
 
*Ref 2: RED interfaces Article* https://docs.sophos.com/nsg/sophos-firewall/19.5/Help/en-us/webhelp/onlinehelp/AdministratorHelp/Network/Interfaces/REDInterfaces/index.html

*Ref 3: RED network configuration*

In a typical configuration, you set up the device at a branch office and connect it to the firewall at the head office.

The RED establishes a VPN tunnel to the firewall. So, anything connected to the RED becomes a part of the network. All traffic in and out of the branch office is routed through the RED. You can apply the same policies across local and remote traffic or create custom policies by location.
![image](https://github.com/user-attachments/assets/c0e771f8-0b3f-443f-87df-c46ab27df4af)
 
## Lab Objectives

-	Configure SD-RED deployment mode (Standard/Split/Tunnel)
-	Establish a secure site-to-site tunnel between headquarters and a remote site
-	Implement traffic routing and network security policies
-	Test connectivity and troubleshoot common issues

## CONFIGURATION STEPS



### How to configure a RED
You can configure a RED appliance or Sophos Firewall as a RED appliance.

##How to configure a RED appliance##

You can connect RED appliances, such as SD-RED, installed in the remote office, to Sophos Firewall installed in the main office.

-	Go to System services > RED.

Enable RED status on Head Office firewall, if it gives error enable default `TCP port 3400` for RED tunnel at head office uplink Inbound and Outbound.
![image](https://github.com/user-attachments/assets/ee12239c-dca1-413e-be97-2e828664ec73)
 

1.	Turn on the RED service, and register Sophos Firewall with the RED provisioning server. This is a one-time action.
![image](https://github.com/user-attachments/assets/e897fed9-7055-49ea-9fd2-e17644b95d0a)
![image](https://github.com/user-attachments/assets/8305d5c4-d081-4b80-906b-8d19a3999dab)
![image](https://github.com/user-attachments/assets/874114ec-dc40-4699-8f83-fa5029f092fb)
 
 
 
Add zones
![image](https://github.com/user-attachments/assets/9d5db706-b8fc-4029-935f-c041a718df8e)
 
Save the configurations
![image](https://github.com/user-attachments/assets/9e05bbc3-0377-49cd-afec-9f69396b2f32)
 
Later we will add this zone to my web tunnel that’s our objective here.
![image](https://github.com/user-attachments/assets/99219333-7e4d-482c-b032-d60d79449803)
 




2.	Configure the RED interface on your Sophos Firewall. 


-	Add an interface for a RED hardware model.

-	Do as follows:

-	1. Go to Network > Interfaces, click Add interface, and select Add RED.
 ![image](https://github.com/user-attachments/assets/bb5fc87b-fcb2-4b42-a6d4-34edba5ac954)


-	2. Enter a branch name.
-	3. Select the type of RED interface from the list.
-	RED 15, 15 (w), and 50 are now end-of-life (EOL). We recommend you use SD-RED 20 or 60.
![image](https://github.com/user-attachments/assets/3dac492e-4329-46f9-8ddf-725ccce57c81)

 
-	4. Specify the RED settings.

-	RED identification number. You can find the ID on the back of the device and on the product packaging
![image](https://github.com/user-attachments/assets/e575ab47-3ba2-42eb-ba4d-972d2868c8e5)
![image](https://github.com/user-attachments/assets/a604c7d3-2402-4edd-a0e3-d61cd91759e8)
![image](https://github.com/user-attachments/assets/c27e9e27-5291-423e-9c27-13797858486d)
 
 
 
Firewall hostname
![image](https://github.com/user-attachments/assets/5429cfe5-3196-4ba5-b071-f5933ab98a03)
![image](https://github.com/user-attachments/assets/2f4ca771-ded8-41ee-b119-449a1fd9bb6d)
![image](https://github.com/user-attachments/assets/4c5ff448-4e1b-446c-b661-75cd72192b4f)
![image](https://github.com/user-attachments/assets/573e4400-1aa8-4ce4-8829-00a85bd2e7e9)
![image](https://github.com/user-attachments/assets/83eb7b48-f3bc-47cc-a75d-6aec942082ec)
 

Specify the RED network settings.
![image](https://github.com/user-attachments/assets/c0ad3bd2-166a-4299-9d1a-cb753d58196c)
 
## RED operation mode

*Ref: Standard/Unified*
![image](https://github.com/user-attachments/assets/e40eff48-ae75-4053-8c6b-0e3371eb3dd3)

 
*Ref: Standard/Split*
![image](https://github.com/user-attachments/assets/8415b90e-b143-46da-9290-78ad1352b35a)
 
*Ref: Transparent/Split*
![image](https://github.com/user-attachments/assets/2ef18bea-2ab6-4974-93af-2adbde148f31)
![image](https://github.com/user-attachments/assets/4067e1ef-cde0-4fee-8e6a-fb08e3533642)
![image](https://github.com/user-attachments/assets/b285dbb9-1dfd-4f1a-9e9b-ba61b5e04098)
![image](https://github.com/user-attachments/assets/4cff59c9-1aa3-422e-a16e-ddf772c5c960)
 

3.	Connect the RED appliance to the internet at the remote site

*Ref: Example*
![image](https://github.com/user-attachments/assets/7711d4be-7b50-4634-af4a-b18f9cef233f)
![image](https://github.com/user-attachments/assets/6f4e2d4a-ea33-4713-999b-8678f7ef7fa7)

You can also connect Sophos Firewall devices in the head and remote offices using a site-to-site RED tunnel.

-	1. Go to System services > RED.
-	2. Turn on the RED service, and register Sophos Firewall with the RED provisioning server, this is a one-time action.
-	3. Configure `firewall 1` as the Firewall RED Server. See Add a RED interface article: https://docs.sophos.com/nsg/sophos-firewall/19.5/Help/en-us/webhelp/onlinehelp/AdministratorHelp/Network/Interfaces/REDInterfaces/REDInterfaceAdd/index.html

-	4. Go to Network > Interfaces. Download the provisioning file for firewall 1.
-	5. Configure `firewall 2` as the Firewall RED Client. Upload the provisioning file.

See Create a site-to-site RED tunnel: https://docs.sophos.com/nsg/sophos-firewall/19.5/Help/en-us/webhelp/onlinehelp/AdministratorHelp/Network/Interfaces/REDInterfaces/HowToArticles/REDCreateSiteToSiteREDTunnel/index.html




