# Task 4: Windows Firewall Configuration Report

This report documents the process of configuring and testing the `Windows Defender Firewall` to control network traffic on a local machine. The objective was to add and test a rule to demonstrate basic firewall management skills.

---

### **1. Objective**

To use the **Windows Defender Firewall with Advanced Security** tool to create a new inbound rule that blocks traffic on a specific port, and then to test that the rule is working correctly.

---

### **2. Tools and Environment**

*   **Operating System:** `Microsoft Windows`
*   **Tool:** `Windows Defender Firewall with Advanced Security`
*   **Testing Utility:** `PowerShell` (using the `Test-NetConnection` cmdlet)

---

### **3. Process and Execution**

The following steps were performed to complete the task.

#### **Step 1: Listing Current Firewall Rules**

I began by opening the `Windows Defender Firewall with Advanced Security` tool and navigating to the **"Inbound Rules"** section. This provided a complete list of all currently active and inactive rules on the system, showing what applications and services are allowed or denied access.

![Rules](https://github.com/user-attachments/assets/ba80d93e-31e8-40d6-acc5-47030404217e)
![Ruless](https://github.com/user-attachments/assets/bd40f3b1-efff-48dc-8537-6e42b05c73c9)


#### **Step 2: Creating a New Rule to Block Telnet (Port 23)**

Next, I created a new inbound rule specifically to block traffic for the `Telnet` service, which operates on `TCP port 23`.

*   **Action:** In the "New Inbound Rule Wizard," I specified the rule type as `Port`.
*   **Protocol and Port:** I set the protocol to `TCP` and the specific port to `23`.
*   **Rule Action:** I selected **`Block the connection`**.
*   **Name:** I named the rule **`Blocked Telnet`** for easy identification.

The new rule was successfully added and appeared at the top of the inbound rules list, as shown in the screenshot below.

![Blocked Telnet](https://github.com/user-attachments/assets/3af8c8a6-c1cb-4262-abc0-26ab603ad0cd)

#### **Step 3: Testing the Firewall Rule**

With the "Block" rule active, the final step was to test if it was actually working. I used the `Test-NetConnection` command in PowerShell to attempt a connection to port 23 on my own machine (`localhost`).

*   **Command Executed:**
    ```powershell
    Test-NetConnection -ComputerName localhost -Port 23
    ```

*   **Result:** The connection attempt **failed**, with the output showing `TcpTestSucceeded: False`. This result confirms that the firewall rule is working exactly as intended—it successfully identified and blocked the traffic destined for port 23.

The screenshot below shows the command and its failed result, providing clear evidence of a successful firewall block.

<img width="767" height="329" alt="Tcp conn failed" src="https://github.com/user-attachments/assets/375baa39-38ff-4a92-950e-4f6e7eaa64b3" />

#### **Step 4: Cleanup**

After the successful test, the `Blocked Telnet` rule was deleted from the firewall to restore the system to its original state.

---

### **4. Conclusion**

This task provided practical, hands-on experience with a fundamental cybersecurity tool. The process demonstrated how a firewall acts as a gatekeeper for network traffic. By creating a specific rule to block `TCP port 23`, I was able to prevent connections to that port, which was verified using a PowerShell test command.

This exercise highlights how firewalls are essential for reducing a system's "attack surface" by allowing administrators to enforce policies on what traffic is permitted and what is denied, thereby protecting the system from unwanted access.
