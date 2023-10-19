# WAF20 - Network Controls (draft)

**NOTE:** 
This content below is supposed to be part of the WAF 20 document, to be embedded in the chapter "WAF>Recommendations>SE:06Network Controls".

https://review.learn.microsoft.com/en-us/azure/well-architected/security/networking?branch=collab-waf-2-0-1

## Introduction / Use case

**Network Controls** will focus on network design, mainly regarding security controls that will help you to filter, block and detect adversaries trying to evade your network.

Bad actors may start an attack in different layers or resources in an IT environment, like starting the attack directly in a VM, or using a compromised credential (identity), or through a vulnerability in your Application or through a SQL injection built against your database. Whatever resource is considered by the attacker, those malicious actions will get something involved with the Network.

Attacks against network environment may happen in different resources of your network topology, such as routers, switches and firewalls as well, using different techniques, starting with a simple network mapping discovery using NMAP tool or intercepting and inspecting your network traffic, also known as "sniffing", ubsing tools such as Wireshark and others.

The good one is that we have many security solutions that may protect you against those practices above and much more. In this use case, we are considering an IT environment, the reference presented in the chapter "Baseline" (add a link here) with some workloads, components, and personas that will help you understand all the recommendations in this chapter, regarding **Network controls**.

![image](https://github.com/rudneir2/WAF20-Network-Controls-Draft-/assets/97529152/b3b88049-64b5-4b71-9808-d8f62796a2c5)

Let's consider the following in the diagram:

1. several personas may be considered in a network attack, including Admins, employees, customer's clients and anonymous attackers. But we have some specific resources that we need to take care about it and consider the right security solutions for your network.
2. different personas may access your on-premises environment through a VPN, or even Azure environment may be connected to your on-premises environment through a VPN resource created on Azure, that may be configured with IPSec protocol for a secure communication.
3. different personas may also have access to your Web applications publicly, but if it configured properly you may have in front of your Web applications, a Web Application Firewall, or WAF, that work to protect you on Layer 7 of network OSI layer.
4. some personas, like Administrators, may have remote access to specific workloads. Let's say Admins need to manage some VMs. This access happens through Layer 4 of network OSI layers, then, you may consider an Azure Firewall with IDP/IDS features to protect your Applications running on Azure.
5. if you consider DDOS a threat, you may have a DDOS protection for your entire VNET.
6. Configure a network topology as "hub-spoke" may deliver a better network topology, more secure and optimized regarding implementation, manageability and costs, which you can have all network security services in the same VNET, protecting many spoke VNETs connected to this Hub VNET.
7. For some services that originally are exposed to internet, like Storage Accounts and Azure SQL DBs, you may consider adding those services into your private network, by using Private Endpoints, that basically create a Network Card (NIC) in your private VNET and is bind with the Azure service.
8. it is important to remember that communication on Azure goes through TLS, so any VM communicating with others VMs or Azure services, will be protected "in-transit".
9. But even with different layers of protection, you may still consider an affordable network security resource, the NSG, Network Security Group, a free of cost resource that may filter TCP/UDP inbound and outbound commnication considering IP and port ranges.
    It is important to mention that part of NSG, is the ASG (Application Security Group), a great resource for network segmentation.

10. Azure resources used by infrastructure like VMs, Storage and Network, like the ones presented in this diagram, such as VNET, plus Azure Network Security services, highlighted in this diagram, may ingest logs on Log analytics then used with a SIEM solution like Microsoft Sentinel.
11. Log Analytics is totally integrated with Microsoft Sentinel and others solutions like Microsoft Defender for Cloud.
12. Microsoft Defender for Cloud delivers many workload protection solution, including Network recommendation for your environment.
13. another great solution for monitoring your Network, regarding your Network controls is about Traffic Analytics, that is configured through Network Watcher, part of Azure Monitor, and aggregate inbound and outbound hits in your subnets, collected by NSG.

**NOTE:**
If you'd like to understand more about any solution described in the diagram, including acronyms, please refer to this table of contents, from the Baseline chapter.
(table to be built)

In the following content, you will find more details about **Network Controls** that you will be able to apply in your environment for a better Security posture.

**from this point on, we could add the current draft content for Network Control**
