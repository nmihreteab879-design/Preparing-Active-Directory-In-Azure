<p align="center">
  <img src="https://i.imgur.com/pU5A58S.png" alt="Microsoft Active Directory Logo"/>
</p>

# On-Premises Active Directory in Azure (Beginner-Friendly Explanation)

This project shows how I created a small “on-premises” Active Directory environment using virtual machines in Microsoft Azure. Even though everything is in the cloud, the setup behaves the same way as a physical company network.  

The goal of this lab was to understand how computers find each other, communicate privately, and use a domain controller for identity and management.

## Technologies Used
- Microsoft Azure (Virtual Machines & Networking)
- Remote Desktop (logging into the VMs)
- Active Directory Domain Services
- Basic Command Prompt tools (ping, ipconfig)

## Operating Systems
- Windows Server 2022 (Domain Controller)
- Windows 10 (Client Computer)

# Overview (Beginner Friendly)

Below are the major steps I completed and **why each one matters**.  
Right after each section, you will see:  
- **Screenshot goes here** (replace with your actual image)  
- A simple explanation of what skill that step demonstrates

This makes your GitHub clear and readable.

# Step 1 — Creating the Resource Group and Virtual Network

<p align="center">
  <!-- Replace the link below with your actual screenshot -->
  <img src="YOUR-SCREENSHOT-1.png" />
</p>

I started by making a **resource group** and a **virtual network**.  
The resource group is just a folder that keeps everything organized.  
The virtual network acts like the private “wiring” that lets the machines talk to each other inside Azure.

**Why this matters (explained simply):**  
This step shows I understand how to set up a safe, private mini-network in the cloud. Every real company uses something like this.

# Step 2 — Creating the Domain Controller VM (DC-1) and Assigning a Static IP

<p align="center">
  <img src="YOUR-SCREENSHOT-2.png" />
</p>

I created a Windows Server virtual machine called **DC-1**. This machine will later become the “domain controller,” which is like the main server that manages users and computers.

I also changed its private IP address to **static** so it never changes.

**Why this matters:**  
Computers need to find the domain controller every time they start. If its address changed, the whole system would break.  
This shows I understand real-world server requirements.

# Step 3 — Logging Into DC-1 and Temporarily Disabling the Firewall for Testing

<p align="center">
  <img src="YOUR-SCREENSHOT-3.png" />
</p>

I connected to DC-1 using Remote Desktop and turned off the firewall temporarily. This was just to make sure the two machines could communicate while I tested the network.

**Why this matters:**  
It shows I understand how to troubleshoot network issues safely.  
(And I also understand that firewalls stay ON in real environments.)

# Step 4 — Creating the Client Machine (Client-1) and Setting Its DNS to DC-1

<p align="center">
  <img src="YOUR-SCREENSHOT-4.png" />
</p>

I created another virtual machine called **Client-1**, which acts like an employee’s computer. I changed its DNS setting so it points to DC-1’s private IP address.

**Why this matters:**  
Active Directory **depends on DNS**.  
If Client-1 can’t ask DNS to locate the domain controller, nothing will work.  
This shows I understand the relationship between DNS and Active Directory.

# Step 5 — Restarting Client-1 So the New Network Settings Take Effect

<p align="center">
  <img src="YOUR-SCREENSHOT-5.png" />
</p>

After changing the DNS, I restarted Client-1 from the Azure portal to make sure the settings were fully applied.

**Why this matters:**  
Many system changes don’t apply until a restart.  
This shows awareness of how Windows networking behaves.

# Step 6 — Testing Connectivity with Ping and Checking DNS with `ipconfig /all`

<p align="center">
  <img src="YOUR-SCREENSHOT-6.png" />
</p>

Once Client-1 restarted, I tested the connection:

- I pinged DC-1 → the ping succeeded  
- I ran `ipconfig /all` → it confirmed DC-1 was now the DNS server

**Why this matters:**  
This demonstrates troubleshooting ability:
- Can Client-1 reach DC-1?  
- Is DNS pointing to the right place?  
- Are the machines communicating correctly?

These are real help desk and system admin skills.

# Skills Demonstrated (Explained for Non-Technical People)

- **Building a private network in Azure:**  
  I created a safe, isolated environment where machines can talk securely.

- **Setting up and preparing a domain controller:**  
  This server becomes the “brain” of a company network.

- **Configuring machines to communicate correctly:**  
  I made sure each machine knew how to find and talk to the others.

- **Understanding how DNS affects authentication:**  
  DNS works like a phonebook. If the phonebook is wrong, nothing connects.

- **Testing and validating network setups:**  
  Using tools like `ping` and `ipconfig` to make sure everything works.

- **Troubleshooting mindset:**  
  I confirmed each step worked before moving on, which is exactly how real IT work is done.






