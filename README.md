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

In this first setting, we have a client virtual machine which we will use to create the directory and set up remote access. We’ll also need the domain controller which will be the server we use to set up our domain system.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/20ca742d-fec6-4e7a-a444-351094a9b97d)

Logged into the Domain Controler to enable ICMPv4 on the Windows firewall.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/5105382d-c2c9-49f2-a5cf-7126a64def49)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/009a2042-adc5-4e6d-8b9f-b91c55cafd9e)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/ccfd3435-0f27-433c-8126-7d591663d0b5)

Log into the client VM to ensure connectivity between the server and Client machine. This is done by sending a ping to the server using its private IP(10.0.0.4).

![image](https://github.com/SedinamA/AD-setup/assets/146953803/81bb39bd-8299-410f-a63e-b98f639e2951)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/4b01a92d-0482-4772-ba87-1990750c64b2)

Installation of the Active Directory Domain Service on DC-Server. Kept pressing "next", then checked the "Active Directory Domain Service" option.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/591e7a5d-06c4-4aab-9247-da192bea2043)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/539f6044-d2af-4e71-a2c9-f107336bdfc3)

Select install 
![image](https://github.com/SedinamA/AD-setup/assets/146953803/b0596ec8-b20c-4835-9209-481bb7b29dfb)

Select close
![image](https://github.com/SedinamA/AD-setup/assets/146953803/7cfd0ed1-e3d6-4848-bcee-6ec1a2bdb072)

click on the flag with the yellow triangular symbol on it. Then select "promote this server to a domain controller" 
![image](https://github.com/SedinamA/AD-setup/assets/146953803/9b2ff95b-29df-421a-8568-e3e6b1825809)

Check "add new forest". 
my created domain is “domainbysed.com”. 
click "next"
![image](https://github.com/SedinamA/AD-setup/assets/146953803/62971cfd-0789-467e-af13-4900d5d711ed)

Password created for the domain on the server.
Keep pressing next until "install" button is available
![image](https://github.com/SedinamA/AD-setup/assets/146953803/f61354fd-2cb3-446e-b9aa-28213c97387d)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/6df9cf16-797e-4642-a90c-1dbbb019821d)

in the Azure portal, the DC-server is then restarted
![image](https://github.com/SedinamA/AD-setup/assets/146953803/f7ca07b0-c64d-455c-bd68-2ee472ecab9f)

Logged back into DC-Server with a new username.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/703fc087-1032-41a2-8edc-932d39bfc38d)

In the “active directory users and computers” (ADUC) the creation of two organizational units (_EMPLOYEES and _ADMINS) can be observed.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/cfbd83c0-502a-4f98-9629-bfbf5a5e7aa2)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/3c518e47-e5ee-43c3-bc28-abd728618029)

In the “_ADMINS” unit an employee account is set up for “Jane Foster” with the username “jane.admin”
![image](https://github.com/SedinamA/AD-setup/assets/146953803/768cd79e-1697-40f6-9c5b-1cd3c4bda2cb)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/36e0b010-7382-4f91-b745-385bed84cbe1)

“jane.admin” was then added to the “Domain Admins” security group. 
![image](https://github.com/SedinamA/AD-setup/assets/146953803/b9539f20-a2dd-4652-903a-df6cd0e6a3ec)

We then close the remote desktop connection with the DC server and log back in with a new username 
![image](https://github.com/SedinamA/AD-setup/assets/146953803/bf973a1c-d0d9-45f0-ae73-d1dcbc0e2173)

From the Azure portal, the Client VM DNS is set to the DC server's private IP and then the client VM is restarted.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/e2e00c0b-b477-467b-a694-4ba0aec192fa)

We then log into the client VM with Remote Desktop and join it to the domain. The computer will restart.
Click "Rename this PC(Advanced)"
![image](https://github.com/SedinamA/AD-setup/assets/146953803/950ae27c-ab15-4b31-bd2e-b3b77ea72821)

select "Change"

![image](https://github.com/SedinamA/AD-setup/assets/146953803/1dc2e8f9-e7de-4bee-98fe-597acb47533a)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/05660895-4be5-44cb-b688-e18bd1cf664d)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/a8b409a0-f564-494f-bd45-0374a263cd87)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/adab9334-05f2-4852-9eef-5066c1927c12)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/c9d19778-f3d4-4329-80a0-8cd67a32e1f0)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/e017bc33-71d8-4cfb-8e6b-b606211eb1ca)

In DC-server we will verify that “Client” shows up in the Active Directory Users and Computers window. This should be in the “Computers” folder on the root of the domain.
![image](https://github.com/SedinamA/AD-setup/assets/146953803/abdded57-e5f8-4bc7-82c7-5d01462a2ba8)

In the Client VM, we setup Remote Desktop for non-admin users. This is done by login back into the VM as admin Jane.
Go to “systems”. Click on “remote Desktop”. Allow “domain users” access to remote desktop.

![image](https://github.com/SedinamA/AD-setup/assets/146953803/5a417627-312f-4d06-8cae-1b40e2ae7d95)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/027ca9d9-3b4b-449e-9742-d9c985d6ea57)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/27e05355-862d-4aab-a328-262a87ce4313)
![image](https://github.com/SedinamA/AD-setup/assets/146953803/45b1aeae-5c93-44a7-9143-a9a54461bc55)
























