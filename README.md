This is the **Task 04** of my internship at **Elevate Labs**. 

**Objective**

Configure and test basic firewall rules to allow or block traffic.

**Tools Used**
Windows Defender Firewall, Windows Powershell

**GUI Rules:**

Step 1: Open the firewall configuration tool (For this, I use Windows Defender Firewall)
* Click **Start** menu
* Open **Windows Defender Firewall with Advanced Security**.

Step 2: Find current firewall rules
* Navigate **Inbound Rules** in Windows defender firewall.
* In this, all current inbound rules are listed with name, group, profile, enabled, etc. (Screenshot-1: New Inbound Rules)

Step 3: Add a rule to block port 23 (Telnet)
* Click **New Rule** from **Actions** section right side of this GUI.
* There is a window that contains program, port, predefined, and custom. Click **Port** from the window and then click **Next**.
* Click **TCP** and type **23** in **specific local ports** column. (This port contains telnet).
* Select **Block the connection** → click Next.
* Click Domain, Private, and Public profiles → click Next.
* Name the rule **Block Telnet Port 23** → click Finish. (Screenshot-2: Added block telnet port 23)

Step 4: Test with PowerShell
* Type the command "Test-NetConnection -ComputerName localhost -Port 23  " in the command prompt.
* Result: **TcpTestSucceeded: False** (Screenshot-3: Test)

Step 5: Remove the test rule
* Go to **Inbound rules** in Windows Defender Firewall, locate Block Telnet Port 23, click **Delete** on the Actions section.

**Commands Used**: Test-NetConnection -ComputerName localhost -Port 23 

**How a Firewall Filters Traffic**

A firewall acts as a network security barrier, inspecting inbound and outbound packets and comparing them to predefined rules.
* Allow rules let traffic through if it matches the criteria (port, protocol, IP).
* Block rules stop traffic from reaching the application or service.
* Filtering can be based on:
    * Port numbers (e.g., 23 for Telnet, 80 for HTTP)
    * Protocols (TCP, UDP, ICMP)
    * IP addresses (source/destination)
* In this test, blocking TCP port 23 stopped all Telnet connections to the system.


  



