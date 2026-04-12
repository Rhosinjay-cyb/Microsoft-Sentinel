## Project Title

Managing Security Operations with Microsoft Sentinel

## Objective

The aim of this project is to deploy Microsoft Sentinel in a log analytics workspace to leverage its SIEM and SOAR capabilities to manage security operations, ranging from collection of logs from various Azure services and resources to remediation of threat with playbooks.

## Tools Used

Microsoft Sentinel (standalone), Microsoft Sentinel in Microsoft Defender


## Lab Setup

* Deployment of Microsoft Sentinel in a log analytics workspace
* Configuration of the forwarding of Azure Bastion logs to the Sentinel Workspace via Diagnostic setting
* Enabling the ingestion of Azure Activity logs to the Sentinel workspace via Azure Activity connector
* Configuration of the collection and forwarding of Windows Security Events from virtual machines to the Sentinel workspace
* Development and implementation of analytics rules using Kusto Query Language queries to enhance threat detection capabilities.
* Implementation of SOAR workflows to support efficient remediation of security incidents.
  
## Architecture Diagram


## Preamble

This project builds upon a previously concluded project on Azure Firewall, and it focuses on the security operations aspect of the security solution, including logging, monitoring, threat detection and incident remediation. Where required, references will be made to the former project; however, all underlying concepts and configurations will be clearly explained to ensure completeness and clarity. 

## Steps Taken

The project commenced with the deployment of Microsoft Sentinel in the Project-workspace (this log analytics workspace was created in the last project and it already contains the Azure Firewall logs).  

![image](Images/SEN.png)

Afterwards, Azure Bastion logs is forwarded to the Sentinel-integrated workspace via diagnostic settings (Project-BST-logs)

![image](Images/BSTL.png)

The Azure Bastion logs are stored in the MicrosoftAzureBastionAuditLogs table in the Sentinel-integrated workspace. It was confirmed that the workspace is now receiving logs from Azure Bastion.

![image](Images/BSTL2.png)

Additionally, Azure activity log which stores the event carried out in the Azure subscription including any updates made on the firewallis forwarded to the sentinel-integrated workspace via Azure Activity connector. The process started with the installation of Azure Activity from content hub and culminated with the configuration of the connector.

![image](Images/AzAC.png)

The Azure activity logs are now visible from the sentinel-integrated workspace as shown below.

![image](Images/AAL.png)

To ingest the logs from the virtual machines to the sentinel-integrated workspace, Window Security Event solution is installed from Content hub.

![image](Images/WSE.png)

Then the Windows Security Event via Azure Monitor Agent (AMA), is configured through the connectors page.

![image](Images/WSE2.png)

A significant step in the configuration of the connector is the creation of a data collection rule (DCR) 
this allows for the specyfing of the 
![image](Images/VM2M.png)

## Findings and Recommendations



## Implementation of Recommendations



## Conclusion


## Future Works




 
