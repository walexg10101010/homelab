# homelab
Documenting personal projects as I learn more about Information Systems and Technology.
Download and install Oracle VirtualBox: https://www.virtualbox.org/wiki/Downloads .
It might be necessary to enter BIOS/UEFI and enable hardware-level CPU virtualization to run virtual machines so make sure to double check, as I had to.
On set up, I didn't specify network adapters. I allocated 4 processors, and about 5GB of memory to the virtual machine. I mounted the Windows Server 2025 ISO https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2025 and loaded up the virtual machine. I followed the on-screen instructions and installed the server OS.
Once that was installed, I configured the network connection as a bridged adapter to the host, receiving an IP from my local router for now. I added the AD DS role and the DNS role to the server, created the homelab.local domain, and promoted the server to the domain controller with DNS.
I went to Users and Groups, and created 4 organizational units: Information Systems, Finance, Operations, and Human Resources which are typically fundamental ERP functional areas.
For email, I decided to test out hMailServer https://www.hmailserver.com/download/ for now. To install hMailServer, I needed first needed .NET 3.5 features so I went to server manager, although control panel is another option for features, and added the .NET 3.5 feature indicating the ISO I had mounted previously as the source.
I proceeded to install hMailServer, indicating homelab.local as the source.
To test the functionality of the email server, I temporarily opened the ports 25, 110, and 143 to allow SMTP, POP3, and IMAP.
I downloaded the email client Mozilla Thunderbird https://www.thunderbird.net/en-US/ to test the email server functionality.
I created a user under Information Systems, and then in hMailServer I linked the user to Active Directory for login. Initially, I had issues logging in to the email server with the user credentials, but this was because hMailServer by default required SSL/TLS authentication. For testing purposes, I removed that, and I was able to login and send an email to myself.
Currently, I am in the processes of cleaning this part up (email), and perhaps trying a different email server (perhaps Stalwart).
