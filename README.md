<h1>Active Directory(AD) Creation </h1>
In this implementation, a set-up of an Active Directory using a virtual server(DC-Server) will be observed. Once created the viability of the active directory will be tested through remote access from a virtual machine(Client-VM).<br />

<h2>Environment and Technology used</h2>

- Microsoft Azure (Virtual Machines)
- Remote Desktop
- Active Directory Domain Service
- PowerShell

<h2>Operating Systems Used </h2>

- HP Windows 11 laptop (Base Computer)
- Windows Server 2022 Virtual Machine
- Windows 10 Virtual Machine

<h2>AD Implementation </h2>

In this first setting, I have a client virtual machine(Client VM) which was used to create the directory connection and set up remote access. Also required was the domain controller (DC-Server), which served as the server I used to set up the domain system.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/20ca742d-fec6-4e7a-a444-351094a9b97d)

I then logged into the Domain Controler to enable ICMPv4 on the Windows firewall.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/5105382d-c2c9-49f2-a5cf-7126a64def49)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/009a2042-adc5-4e6d-8b9f-b91c55cafd9e)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/ccfd3435-0f27-433c-8126-7d591663d0b5)

After the last step, I logged into the client VM to ensure connectivity between the server and Client machine. This was done by sending a ping to the server using its private IP(10.0.0.4).

![image](https://github.com/SedinamA/AD-setup/assets/146953803/81bb39bd-8299-410f-a63e-b98f639e2951)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/4b01a92d-0482-4772-ba87-1990750c64b2)

Installation of the Active Directory Domain Service on DC-Server. Kept clicking "next", then checked the "Active Directory Domain Service" option.

![image](https://github.com/SedinamA/AD-setup/assets/146953803/591e7a5d-06c4-4aab-9247-da192bea2043)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/539f6044-d2af-4e71-a2c9-f107336bdfc3)

Selected install 

![image](https://github.com/SedinamA/AD-setup/assets/146953803/b0596ec8-b20c-4835-9209-481bb7b29dfb)

Selected close

![image](https://github.com/SedinamA/AD-setup/assets/146953803/7cfd0ed1-e3d6-4848-bcee-6ec1a2bdb072)

clicked on the flag with the yellow triangular symbol on it. Then selected "promote this server to a domain controller" 

![image](https://github.com/SedinamA/AD-setup/assets/146953803/9b2ff95b-29df-421a-8568-e3e6b1825809)

Checked "add new forest". 
my created domain was “domainbysed.com”. 
then I clicked on "next" button.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/62971cfd-0789-467e-af13-4900d5d711ed)

Password was then created for the domain on the DC-server.
Kept pressing next until the "install" button was available
![image](https://github.com/SedinamA/AD-setup/assets/146953803/f61354fd-2cb3-446e-b9aa-28213c97387d)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/6df9cf16-797e-4642-a90c-1dbbb019821d)

in the Azure portal, DC-server was then restarted
![image](https://github.com/SedinamA/AD-setup/assets/146953803/f7ca07b0-c64d-455c-bd68-2ee472ecab9f)

after the restart was completed, I Logged back into DC-Server with a new username.

![image](https://github.com/SedinamA/AD-setup/assets/146953803/703fc087-1032-41a2-8edc-932d39bfc38d)

In the “active directory users and computers” (ADUC) the creation of two organizational units (_EMPLOYEES and _ADMINS) can be observed.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/cfbd83c0-502a-4f98-9629-bfbf5a5e7aa2)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/3c518e47-e5ee-43c3-bc28-abd728618029)

In the “_ADMINS” unit an employee account was set up for “Jane Foster” with the username “jane.admin”
![image](https://github.com/SedinamA/AD-setup/assets/146953803/768cd79e-1697-40f6-9c5b-1cd3c4bda2cb)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/36e0b010-7382-4f91-b745-385bed84cbe1)

“jane.admin” was then added to the “Domain Admins” security group. 
![image](https://github.com/SedinamA/AD-setup/assets/146953803/b9539f20-a2dd-4652-903a-df6cd0e6a3ec)

I then closed the remote desktop connection with the DC server and log back in with a new username once more 
![image](https://github.com/SedinamA/AD-setup/assets/146953803/bf973a1c-d0d9-45f0-ae73-d1dcbc0e2173)

From the Azure portal, the Client VM DNS was set to the DC server's private IP and then the client VM was restarted.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/e2e00c0b-b477-467b-a694-4ba0aec192fa)

I then logged back into the client VM with Remote Desktop and joined "Client-VM" to the domain. The computer will restart.
Clicked on "Rename this PC(Advanced)"
![image](https://github.com/SedinamA/AD-setup/assets/146953803/950ae27c-ab15-4b31-bd2e-b3b77ea72821)

selected "Change"

![image](https://github.com/SedinamA/AD-setup/assets/146953803/1dc2e8f9-e7de-4bee-98fe-597acb47533a)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/05660895-4be5-44cb-b688-e18bd1cf664d)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/a8b409a0-f564-494f-bd45-0374a263cd87)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/adab9334-05f2-4852-9eef-5066c1927c12)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/c9d19778-f3d4-4329-80a0-8cd67a32e1f0)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/e017bc33-71d8-4cfb-8e6b-b606211eb1ca)

In the DC-server I verified that “Client-VM” showed up in the "Active Directory Users and Computers" window. Located in the “Computers” folder on the root of the domain.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/abdded57-e5f8-4bc7-82c7-5d01462a2ba8)

In the Client VM, I setup Remote Desktop for non-admin users. This was done by logging back into the VM as admin Jane.
Went to “systems”. Clicked on “remote Desktop”. Allowed “domain users” access to remote desktop.

![image](https://github.com/SedinamA/AD-setup/assets/146953803/5a417627-312f-4d06-8cae-1b40e2ae7d95)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/027ca9d9-3b4b-449e-9742-d9c985d6ea57)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/27e05355-862d-4aab-a328-262a87ce4313)

selected "ok"

![image](https://github.com/SedinamA/AD-setup/assets/146953803/45b1aeae-5c93-44a7-9143-a9a54461bc55)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/df11bc30-fc50-477e-ac75-0d15aecb078f)

In DC-server, using PowerShell_ise(run as administrator) I loaded script to create multiple sample users and provided a password to log in to the directory through Client-VM.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/17d79381-db98-4ab4-9452-15297f2585c4)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/1e1d378d-db30-44e6-904c-97721083f4fa)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/f69d215d-17de-4cb5-9059-19d7fa8e26e2)

When completed I open the ADUC (Active Directory Users and Computers) and select a sample user to log into Client VM with.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/ec5dc725-bbf4-47fb-a536-9dc27c5c0803)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/a426e450-0037-400c-9e86-b674e8724f2b)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/0ffe1ef8-c08e-429b-8a3c-662ecf80d1df)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/c38d8987-851e-4aaf-b597-aa27178bceb0)

Now an Active Directory for domainbysed.com has been created.





























