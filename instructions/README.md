# LAB 710: Provisioning and Configuring Windows 365 for Agents

In this lab, you will learn how to Provision and connect to Windows 365 Cloud PC's.

This manual will guide you, step by step, through the whole process. Let's get started!

---

## Logon to the Lab VM

Log in to your Lab Virtual Machine with the following credentials:
- **Username: ++LabUser++**

- **Password: +++Pa$$w0rd+++**

>[!note] In the VM, click the **Password** field then click the green password text above to have it typed out for you!

---
## Finished?

- [] I am logged in to the VM

When you're ready, check the box above and click **Next >** below!
===

Let's log in to the Windows App with the lab tenant credentials.

---
## Launch the Windows App and connect

- Launch the **Windows App** by clicking its icon from the Taskbar.
- **Sign in** with your Lab Tenant Username
    +++@lab.CloudCredential(LAB710CredPool).Username+++
- Click **Next**
- Enter the **Password** for your Lab Tenant User
    +++@lab.CloudCredential(LAB710CredPool).Password+++
- Click **Sign In**

- If prompted for a tour of the Windows App, click **Skip** and click **Next** through the walk-throughs until finished.
- You will see your provisioned Cloud PC. Click **Connect.**
- If prompted, please add your password.
- If prompted to **Allow Remote Desktop Connection**, select **YES**
- You will connect to and log on to your cloud PC automatically in full screen.

You will complete the rest of the lab from within the Windows 365 Cloud PC.
---

## Finished?

- [ ] I am logged in to my cloud pc.

When you're ready, click **Next >**
===


## Login to the Entra Portal and Verify Agent Identity

- Launch the **Edge browser** by clicking its icon from the Desktop or Taskbar. 

- If prompted with the setup page, click **Confirm and Continue. **
- Then select ** Continue without Google data. **
- Click **Contine** twice and **Finish **

- In the browser open the Entra Portal <br> +++https://entra.microsoft.com+++

- **Sign in** with your Lab Tenant Username <br>  +++@lab.CloudCredential(LAB710CredPool).Username+++

- Click **Next**

- Enter the **Password** for your Lab Tenant User
    +++@lab.CloudCredential(LAB710CredPool).Password+++
- Click **Sign In**

- You will likley get prompted to set up multi-factor authentication through security defaults. When you see **Action Required ** click **Next** to set up MFA.
- Follow the prompts to install and set up **Microsoft Authenticator** on your phone.
- Follow the steps to add and verify the account on your device.
- Once Authenticator has been added, click **Done.**
- If prompted to stay signed in, select ** Yes.**

On the left-hand pane, you may need to adjust the view to see the menu options.

- In the Entra portal, go to Agents → Agent Blueprints and verify the **PAW Ignite Lab Blueprint** blueprint is listed. 

- Once you have verified the blueprint is there, close the browser window.

When you're ready, click **Next >**

---
## Finished?

- [] I have verified the agent blueprint. 
===

## Login to the Microsoft Admin Center Portal and Create a Licensed Agent Instance

- Launch the **Edge browser** by clicking its icon from the Desktop or Taskbar.

- The browser will open the Intune portal for you <br> +++https://admin.cloud.microsoft+++

- If prompted **Sign in** with your Lab Tenant Username <br>  +++@lab.CloudCredential(LAB710CredPool).Username+++

- Click **Next**

- Enter the **Password** for your Lab Tenant User
    +++@lab.CloudCredential(LAB710CredPool).Password+++
- Click **Sign In**
- 
- When prompted to **Stay signed in**, click **Yes**

- You may be prompted to configure MFA. Please configure MFA for the lab. You will be able to remove this account from Authenticator when you are finished, and the user account and authentication method will be deleted by the lab proctor

You should now see the **Microsoft Admin Center.**

- On the left-hand side, select **Agents** and then **All Agents **

- In the search/AI search bar, Type "Playground" and select **Enter**

- You should see the same Windows 365 Playground Agent Blueprint that was in the Entra console. 

- Select the instance. The details will load.

- Select the button to **Add Instances **

- In the Agent Instance identity detail window, enter the following:

- ** Instance Display Name ** - enter %USERNAME%-PGA (where USERNAME is your lab username followed by -PGA)
- ** Agent Instance alias ** - enter %USERNAME%-PGA (where USERNAME is your lab username followed by -PGA)
- ** Owner/Reports to ** - select your lab username from the list.

- Click ** Add Instance **

- When the instance has been added, select **Close.**

- Click the **X** in the upper right corner to close out of the details pane.

---
## Finished?

- [] I have created the Agent instance identity.


===

## Login to the Intune Console

- If not already opened, launch the **Edge browser** by clicking its icon from the Desktop or Taskbar.

- Navigate to the Intune portal: <br> +++https://intune.microsoft.com+++

- **Sign in** with your Lab Tenant Username <br>  +++@lab.CloudCredential(LAB710CredPool).Username+++

- Click **Next**

- Enter the **Password** for your Lab Tenant User
    +++@lab.CloudCredential(LAB710CredPool).Password+++
- Click **Sign In**
- 
- When prompted to **Stay signed in**, click **Yes**

- You may be prompted to configure MFA. Please configure MFA for the lab. You will be able to remove this account from Authenticator when you are finished, and the user account and authentication method will be deleted by the lab proctor

- You should now see the **Intune Console.**

- NOTE: Your access will be limited because you are only an AI Administrator and a Windows 365 Administrator.

- Let's create a Provisioning Policy that will be used to create your own Cloud PC.

Follow these steps in the **Intune admin center**.

---
## Create a Provisioning Policy

- Click on **Devices** from the menu on the left side of the portal

- Under **Manage Windows 365 Cloud PCs** click **Provision Cloud PCs**

- Click the **Provisioning policies (Agents)** tab [MAKE SURE YOU ARE SELECTING THE AGENT PROVISIONING TAB]

- Click **Create policy (Agents)**

### General

- **Name** the policy "+++Cloud PCs for @lab.CloudCredential(LAB710CredentialPool).User+++ Agent Instance"

- Leave the **Description** blank

- For **Billing Plan** select **W365A Billing Policy for Lab 2026**
- ALways available Cloud PCs count select **2**
- 
- For **Geography**, select **US West**

- Click **Next** to complete the General tab

### Agents

- Click ** Add Agent User**
- Search for the Agent Instance you created earlier in the lab. Only select that agent instance. Enter %USERNAME%-PGA (where USERNAME is your lab username followed by -PGA)
- Click **Save **
- Click **Next**


### Image
- Leave the defaults and click **Next**

>[+] Default Values
- **Image type** = **Gallery image**
- Selected Image = **Windows 11 Enterprise + Microsoft 365 Apps 26H2**

### Configuration
- Leave the defaults and click **Next**

>[+] Default Values
- **Language & Region** = **English (United States)**
- **Select grouping type** = *UN*-checked
 
### Scope tags
- Leave the defaults and click **Next**

>[+] Default Values
- **Scope Tags** = **Default**

### Review + create
- Review the settings 
- Click **Create** to finish creating the Provisioning Policy for Agents

NOTE: Provisioning will take a while. You will see the status at **Creating** until complete.

---
## Finished?

- [] I have Created and Assigned the Provisioning Policy for Agents

When you're ready, click **Next >**
===

---
## Using Opal - Microsoft's Computer-use Agent

[In this exercise, we will use a pre-existing computer use agent that already has a set of provisioned agentic-use Cloud PCs while waiting for the cloud PCs from the previous exercise to complete.]


## Login to the Microsoft Admin Center Portal and Create a Licensed Agent Instance

- Launch the **Edge browser** by clicking its icon from the Desktop or Taskbar.

- The browser will open the Intune portal for you <br> +++https://admin.cloud.microsoft+++

- If prompted **Sign in** with your Lab Tenant Username <br>  +++@lab.CloudCredential(LAB710CredPool).Username+++

- Click **Next**

- Enter the **Password** for your Lab Tenant User
    +++@lab.CloudCredential(LAB710CredPool).Password+++
- Click **Sign In**
- 
- When prompted to **Stay signed in**, click **Yes**

- You may be prompted to configure MFA. Please configure MFA for the lab. You will be able to remove this account from Authenticator when you are finished, and the user account and authentication method will be deleted by the lab proctor

You should now see the **Microsoft Admin Center.**

- On the left-hand side, select **Agents** and then **All Agents **

- In the search/AI search bar, Type "Opal" and select **Enter**

- You should see the Opal Agent agent template. 

- Select the template. The details will load.

- Select the button to **Add Instances **

- In the Agent Instance identity detail window, enter the following:

- ** Instance Display Name ** - enter %USERNAME%-Opal (where USERNAME is your lab username followed by -PGA)
- ** Agent Instance alias ** - enter %USERNAME%-Opal (where USERNAME is your lab username followed by -PGA)
- ** Owner/Reports to ** - select your lab username from the list.

- Click ** Add Instance **

- When the instance has been added, select **Close.**

- Click the **X** in the upper right corner to close out of the details pane.

---
## Finished?

- [] I have created the Opal Agent instance identity.

## Using the Opal Agent App

- Open up an Edge Browser if one is not already opened.

- Connect to +++https://opal.frontier.microsoft365.com+++

- Click the **Sign in** Button

- If prompted, **Sign in** with your Lab Tenant Username <br>  +++@lab.CloudCredential(LAB710CredPool).Username+++

- Click **Next**

- Enter the **Password** for your Lab Tenant User
    +++@lab.CloudCredential(LAB710CredPool).Password+++
- Click **Sign In**
- 
- When prompted to **Stay signed in**, click **Yes**

- You are now in the Opal Portal. In the field where it says ** Describe the work you want Opal to do for You ** Type in the following prompt:

` 1. Navigate to https://computerusedemos.blob.core.windows.net/web/Contoso/index.html
2. Register this new invoice - source is located here - https://aka.ms/cua-invoice
3. Submit it without asking for confirmation.
 `


- Click ** Up Arrow ** to execute the prompt.

- You will see two panes appear: ** Activity** and ** Plan**

- You will see an additional screen called **Computer** - this is the Windows 365 for Agents Cloud PC checked out to perform your task.

- Because single-sign-on was not configured, you will need to click ** Take Control** and then click ** Sign In**

- If prompted, **Sign in** with your Lab Tenant Username <br>  +++@lab.CloudCredential(LAB710CredPool).Username+++

- Click **Next**

- Enter the **Password** for your Lab Tenant User
    +++@lab.CloudCredential(LAB710CredPool).Password+++
- Click **Sign In**

- Then you will need to click the **Return Control** button

- You will be able to see the computer complete your task in the Live Computer window.

- At some point, you will see a message that says ** Opal needs your attention**

-You will need to click ** Take Control** on the computer window and then within the cloud PC, you will need to click ** Submit Invoice **

- Then click the ** Return Control ** button to return control.

- When the work has been completed, select ** Return computer to the pool. ** 

---
## Finished?

- [] I have completed the Opal Task

When you're ready, click **Next >**

===

---
## Verify your Cloud PC Pool is ready

- In the Intune Console, click the ** Devices** blade in the left-side corner.
- under ** Manage Windows 365 Cloud PCs** select ** Provision Cloud PCs**

- Under the tab ** Provisioning Policies (Agents) ** verify your provisioning policy has been completed. The ** Status** should say ** Available **

- Now, to verify that the pool is actually ready, you will need to double-click on the provisioning policy to get ** Session Usage ** information. 
- When you see the number of ** Available Sessions ** is at 1 or 2, you are ready.

---
## Finished?

- [] I have my Cloud PCs in a provisioned status

When you're ready, click **Next >**

===

---
## Enable a chat with agent in Microsoft Teams

- If not already open, launch the **Edge browser** by clicking its icon from the Desktop or Taskbar.

- Navigate to <br> +++https://teams.cloud.microsoft+++

- If prompted **Sign in** with your Lab Tenant Username <br>  +++@lab.CloudCredential(LAB710CredPool).Username+++

- Click **Next**

- Enter the **Password** for your Lab Tenant User
    +++@lab.CloudCredential(LAB710CredPool).Password+++
- Click **Sign In**

- Under **Chats** look for your created Playground Agent Instance.

- Select it to start a chat session.

[You will begin communicating with the computers via the Foundry Playground Agent through the WIndows 365 for AGents MCP Server. You may have to repeat some of the prompts.]

[You will also be prompted for Live View when available. You can choose to watch live or view periodic screenshots.]

Try out some of these prompts:

`Hello`

` Check out a Cloud PC for me `

`Take a screenshot of the Windows 11 Desktop`

`Launch the Edge Browser, navigate to https://msn.com and tell me the top headlines `

`send an email to [My Email Address] saying hello1

`send a Teams chat message to another Lab user [USERNAME] 



## Finished?

- [] I have finished my agent chat session.

When you're ready, click **Next >**

===
# Thank you

We appreciate you taking the time to go through this lab.  Feel free to linger, try it again, or ask any questions from the lab proctors.

===
## All Done
You're all done!
