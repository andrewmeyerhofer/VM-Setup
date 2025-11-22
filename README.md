<p align="center">
<img width="332" height="220" alt="image" src="https://github.com/user-attachments/assets/19cfbbb3-4489-49f8-bf73-cae02da402ef" />



</p>

<h1>Virtual Machine Creation and Setup for Active Directory Projects</h1>
In this project, my main goal was to create two virtual machines using Microsoft Azure. These VMs will serve as my Domain Controller (dc-1) and Client computer (Client-1) respectively in all my Active Directory projects. I went through the steps of creating a resource group, virtual network, and two virtual machines in Azure, as well as disabling the Windows firewall on dc-1 and joining the domains of both VMs.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Windows PowerShell

<h2>Operating System and Server Used</h2>

- Windows Server 2022
- Windows 11 (24H2)

<h2>VM Creation and Setup Process</h2>

<p>
<img width="1818" height="721" alt="image" src="https://github.com/user-attachments/assets/d67a6fc9-69d1-45ca-b4de-0f686505a617" />

</p>
<p>
I started by creating a resource group in Microsoft Azure. 
</p>
<br />

<p>
<img width="963" height="537" alt="image" src="https://github.com/user-attachments/assets/a77c5d8d-88f6-4b57-bccf-1ebfa9abed2c" />

</p>
<p>
In the creation screen, I chose the subscription I wanted to use, named the resource group, and chose the region. After the information was inputted, I pressed review/create.
</p>
<br />

<p>
<img width="982" height="795" alt="image" src="https://github.com/user-attachments/assets/3912b30e-5e47-4414-a53c-7e0448e31220" />


</p>
<p>
I then looked up "Virtual Network" in the Azure search bar, and clicked the create button. After entering the correct details and giving the Vnet a name, I clicked review/create.
</p>
<br />

<p>
<img width="1445" height="790" alt="image" src="https://github.com/user-attachments/assets/27af529d-d3c9-4344-bd83-79a3681e3a9c" />

</p>
<p>
Next, I searched for "Virtual Machine" then clicked create, choosing the first option for a basic virtual machine. I entered the details and named this VM "dc-1" (Domain Controller 1). I used this VM to simulate a Domain Controller in the upcoming Active Directory Projects.
</p>
<br />

<p>
<img width="981" height="758" alt="image" src="https://github.com/user-attachments/assets/e43ebe78-982b-42e5-80df-bbd595677b27" />

</p>
<p>
I then set the Image and Size of the VM, and created a username and password.
</p>
<br />

<p>
<img width="997" height="795" alt="image" src="https://github.com/user-attachments/assets/140a432c-b2d6-4049-bc98-8ee6de0631da" />

</p>
<p>
Next, I went to the Networking tab and assigned the Vnet I created to this VM. I kept all the other settings for the VM at their default, then clicked review/create.
</p>
<br />

<p>
<img width="1056" height="788" alt="image" src="https://github.com/user-attachments/assets/4af22b56-fb36-46d5-b614-377a807bb47b" />

</p>
<p>
After the dc-1 VM was created, I went through the same VM creation process again. This time I created a VM called "client-1," which will serve as my end-user for the Active Directory projects. 
</p>
<br />

<p>
<img width="970" height="786" alt="image" src="https://github.com/user-attachments/assets/2b1e7304-ff0b-4f5b-8bf3-a4031cd48bf6" />

</p>
<p>
I then set the Image and Size for the VM, this time configuring it like a common end-user's computer. I Also set a username and password and put this VM in the Active-Directory-Vnet. Everything else was left default or the same as dc-1.
</p>
<br />

<p>
<img width="1441" height="685" alt="image" src="https://github.com/user-attachments/assets/06a3651e-b145-4532-b73e-ac3b99b90db8" />

</p>
<p>
Next, I needed to make the Private IP-address for dc-1 static so I could configure it as the DNS server for client-1. I clicked the dc-1 VM and went to the Network Settings tab. Once there, I clicked the link to edit the Network Interface Card (NIC).
</p>
<br />

<p>
<img width="1893" height="731" alt="image" src="https://github.com/user-attachments/assets/6ceaac17-4fa8-43bd-8f95-2cae24c8052a" />

</p>
<p>
I then clicked the link for "ipconfig1" which opened the IP configuration edit tab. I changed the private IP address allocation from dynamic to static then clicked the save button.
</p>
<br />

<p>
<img width="1077" height="145" alt="image" src="https://github.com/user-attachments/assets/c0ff6537-a939-45f3-a872-9cc12e4380c6" />

</p>
<p>
The Private IP address is now listed as static.
</p>
<br />

<p>
<img width="1838" height="555" alt="image" src="https://github.com/user-attachments/assets/5b273339-82c3-4e00-a0e1-6e3a5f3699ff" />

</p>
<p>
Next, I logged into the dc-1 VM using remote desktop. I entered the public IP address into Windows remote connection, then logged in with the username and password I created.
</p>
<br />

<p>
<img width="517" height="261" alt="image" src="https://github.com/user-attachments/assets/5398e708-7f7d-4ebf-8925-d9e1b503ac57" />

</p>
<p>
Upon logging into dc-1, Server Manager imediately opened. From here, I needed to disable the Windows firewall settings on the VM (not smart in real life, just for the sake of this project). I opened "Run" from the start menu and typed wf.msc. 
</p>
<br />

<p>
<img width="1303" height="925" alt="image" src="https://github.com/user-attachments/assets/94debaad-8b9b-4be8-83f3-5ec4f4e4cfb8" />

</p>
<p>
Windows Defender Firewall with Advanced Security opened.
</p>
<br />

<p>
<img width="1301" height="912" alt="image" src="https://github.com/user-attachments/assets/cf70b3ff-f6d1-485a-9075-bd75ae282ead" />

</p>
<p>
From there, I clicked the "Windows Defender Firewall Properties" button and selected off in the dropdown for firewall state (in the Domain Profile tab). I then went to the tabs for Public and Private profiles and selected off as well. Finally, I clicked Apply and OK to save the setting changes.
</p>
<br />

<p>
<img width="1617" height="731" alt="image" src="https://github.com/user-attachments/assets/816cf33e-b9e4-4539-a0ea-9ee638b6b6ec" />

</p>
<p>
Next, I exited the VM and went back to Azure so I could configure the DNS server for client-1. I started by copying dc-1's private IP address from it's VM settings. After that, I went to the network settings of client-1 and clicked the NIC link. Finally, I went to the DNS servers section and pasted dc-1's private IP address as a custom DNS server. Doing this joined the domain of both VMs.
</p>
<br />

<p>
<img width="1512" height="400" alt="image" src="https://github.com/user-attachments/assets/6ba1e783-fd9a-4a55-873c-eda07374e3ff" />

</p>
<p>
I then went to the VM overview menu and selected the restart option for client-1.
</p>
<br />

<p>
<img width="1762" height="583" alt="image" src="https://github.com/user-attachments/assets/7098dbcb-ff0e-4400-9d44-3cd12586ba8f" />

</p>
<p>
Now that everything was configured, I logged into client-1's VM in order to attempt a ping of dc-1. 
<br />

<p>
<img width="1177" height="542" alt="image" src="https://github.com/user-attachments/assets/4f83d757-ac11-45c2-b74d-4acfa133de1b" />

</p>
<p>
Once I was in client-1, I opened Powershell and pinged the private IP address of dc-1. The ping succeeded. 
</p>
<br />

<p>
<img width="1186" height="782" alt="image" src="https://github.com/user-attachments/assets/1d65c6f0-3b67-45d7-a991-f3980bd60284" />

</p>
<p>
Finally, I used the ipconfig /all command and 10.0.0.4 showed up successfully as the DNS server. This concludes the VM setup project.
</p>
<br />
