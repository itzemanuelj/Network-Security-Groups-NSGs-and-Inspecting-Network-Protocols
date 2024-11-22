<p align="center">
<img src=" height="40%" width="60%" alt="Logo"/>
</p>

# Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines

This tutorial demonstrates how to inspect network traffic between Azure Virtual Machines using **Wireshark** and how to experiment with **Network Security Groups (NSGs)** to manage traffic rules.

---

## Environments and Technologies Used
- **Microsoft Azure (Virtual Machines/Compute)**
- **Remote Desktop**
- **Wireshark (Protocol Analyzer)**

## Operating Systems Used
- **Windows 10 (21H2)**
- **Ubuntu Server 20.04**

---

## List of Prerequisites
- Active Azure account with permissions to create resources
- Access to Remote Desktop (e.g., Microsoft RDP)
- Internet-connected computer

---

## Installation Steps

### Step 1: Create Resources  
1. Create a Resource Group in Azure.  
2. Add two virtual machines (VMs):  
   - **VM1**: Windows 10  
   - **VM2**: Ubuntu Server  
3. Ensure both VMs are part of the same virtual network.  

![1]()
![2]()
![3]()
<br>

### Step 2: Configure VMs  
1. Connect to **VM1** via Remote Desktop using its **Public IP Address**.  
2. Install **Wireshark** on VM1.  
3. Open PowerShell on VM1 and ensure you can ping VM2 using its **Private IP Address**.  

![1]()
![2]()
![3]()
<br>

### Step 3: Capture and Analyze ICMP Traffic  
1. In **Wireshark**, start capturing packets.  
2. Filter by **ICMP** to observe ping requests and responses.  
3. Use `ping [private IP]` from VM1 to VM2.  

![1]()
![2]()
![3]()
<br>

### Step 4: Experiment with NSGs  
1. In Azure, open **Network Security Groups** for VM2.  
2. Create a new rule to block ICMP traffic:  
   - Set the priority to `200` and deny ICMP from all sources.  
3. Observe how ping requests now time out.  
4. Edit the rule to allow ICMP again.

![1]()
![2]()
![3]()
<br>

### Step 5: Inspect Other Traffic  
1. **SSH Traffic**:  
   - SSH into VM2 from VM1 using `ssh [private IP]`.  
   - Observe traffic with **tcp.port == 22** in Wireshark.  

![1]()
![2]()
![3]()
<br>

2. **DNS Traffic**:  
   - Use `nslookup www.google.com` on VM1.  
   - Filter by **udp.port == 53** in Wireshark.  
![1]()
![2]()
![3]()
<br>


3. **RDP Traffic**:  
   - Use **tcp.port == 3389** to view Remote Desktop traffic.  

![1]()
![2]()
![3]()
<br>

>! For more details, visit the [Azure](add).


---

## FAQ  
**Q: What are Network Security Groups?**  
**A:** NSGs are Azure's firewall rules that control inbound and outbound traffic to resources.  

**Q: Why use Wireshark for Azure VMs?**  
**A:** Wireshark provides a detailed view of network traffic for analysis and troubleshooting.  

---

## Conclusion  
🎉 Congratulations! You’ve successfully inspected traffic between Azure VMs and configured Network Security Groups. This knowledge helps you secure and optimize cloud-based environments. 🎉


