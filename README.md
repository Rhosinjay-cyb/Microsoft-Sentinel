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
this allows for the specyfing of the target resources (VMs) and the events to collect from it.

![image](Images/VM2M.png)

The completion of DCR automatically installs a AzureMonitorWindowsAgent extension on the VMs.

![image](Images/SUC2.png)

Note: If the DCR is created within the Microsoft Sentinel theWindows event log data will be stored in the SecurityEvent table, but if the DCR is created in the DCRs environment the event will be stored in the Event table without specialized security solution.

With the completion of the configuration of the connector, the staus of the connector now changes to connected, meaning, the agents are now installed on the target resources and are now ready to start collecting logs for fowarding to the Sentinel-integrated workspace. The images also features both the table management and DCR properties.

After the configuration was completed, I noticed the workspace wasn't receving logs despite the status of the connector showing connected. With my fervent troubleshoot, I realised the VMs are behind a firewall (In the last project the firewall was deployed to control the outbound traffic of the VMs, thus affecting the ability of the agent on the VMs to send logs to the Sentinel-integrated workspace). Allowing the firewall to grant access to the traffic requires understanding how traffic is routed from the agents to the workspace to know which service to pass. 

![image](Images/SC-WSE.png)

## Findings and Recommendations



## Implementation of Recommendations



## Conclusion


## Future Works




 
