---
# User change
title: "Getting Started with Microsoft Azure"

weight: 3 # 1 is first, 2 is second, etc.

# Do not modify these elements
layout: "learningpathall"
---
[Microsoft Azure](https://azure.microsoft.com/) is a public cloud computing platform. 

As with most cloud service providers, Azure offers a pay-as-you-use [pricing policy](https://azure.microsoft.com/en-us/pricing/), including a number of [free](https://azure.microsoft.com/en-us/free/) services.

This guide is to help you get started with [Virtual Machines](https://azure.microsoft.com/en-us/products/virtual-machines/), using Arm-based [Ampere](https://azure.microsoft.com/en-us/blog/azure-virtual-machines-with-ampere-altra-arm-based-processors-generally-available/) processors. This is a general-purpose compute platform, essentially your own personal computer in the cloud.

Full [documentation and quickstart guides](https://learn.microsoft.com/en-us/azure/virtual-machines/) are available.

## Create an account

Before you begin, create an account. For a personal account, click on `Free account` or `Try Azure for free` on the [Azure homepage](https://azure.microsoft.com), and follow the on-screen instructions to log in or register as a new user. You can use an existing Microsoft account if you have one.

If using an organization's account, you will likely need to consult with your internal administrator.

Once logged in, you will be presented with the [Azure portal](https://portal.azure.com).

## Create your Virtual Machine (VM) instance

Locate [Virtual Machines](https://portal.azure.com/#view/HubsExtension/BrowseResource/resourceType/Microsoft.Compute%2FVirtualMachines) from the list of `Azure Services`, then click `Create` > `Azure virtual machine`.

You will be presented with the `Create a virtual machine` dialog.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617724-651be04c-2002-4906-9dcc-4de5488d3793.PNG "Create an Azure virtual machine")

## Project details

This section is used to separate instances, usually for internal budgeting or access permissions. 

If a `Resource group` to contain your VMs does not yet exist, click on `Create new`. If you do not create a group, a new one will automatically be created based on your first VM name.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235624790-48c0757f-1451-4e07-a56a-1cb69d54bd7d.PNG "Select or create a Resource group")

## Instance details

This section defines key configuration details of the virtual machine.

### Virtual machine name

Give your virtual machine (VM) a meaningful, but arbitrary name. This is especially useful if you intend to create multiple VMs.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235648745-03e88576-a673-4be9-9e9d-ba14631bb5d3.PNG "Specify a name for the virtual machine")

### Region

This is the location of the server where your VM will reside. While it is generally recommended to select a region closest to your location, not all regions may support Arm-based servers. You may need to change region to get access to such a server.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617809-148d1860-571e-4816-807a-28cadb5b89ce.PNG "Select an appropriate region")

### Availability options / Security type

These are reliability and security settings. They can generally be left as default.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235648749-becadea7-7452-4389-af47-9f013b5440f2.PNG "Select Availability options and Security type if necessary")

### Image

This is the operating system that will run on your VM. Select the appropriate one from the pull-down. Some will have additional pricing associated with them. 

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617811-ea68be13-ae53-44c5-8711-35d004f078dd.PNG "Select an image available for Arm VMs")

Not all are available for Arm VMs. To filter, click on `See all images`, then select `Arm64` from the `Image Type` filter.

![alt-text #center](https://user-images.githubusercontent.com/97123064/243472645-f5dbb211-43c3-4573-afbd-067e388ad7b4.png "Select the 'Arm64' image type")

You can then select a particular version of your preferred OS from the `Select` pull-down of that OS tab.

![alt-text #center](https://user-images.githubusercontent.com/97123064/243473546-360f8003-0f43-4dda-871c-b4b31a29330d.png "Select an image version")

Note that if a `Windows` operating system is selected, the user must have an appropriate license. See the [Azure documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/windows-desktop-multitenant-hosting-deployment) for information.

### VM architecture

If not enabled automatically based on the above image, select `Arm64` for an Arm-based operating system. This will update the `Size` pull-down (see below) to present Arm-based servers.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617744-290da158-b092-4357-ab67-ee0ff7f1ac43.PNG "Choose the 'Arm64' VM architecture")

### Run with Azure Spot discount

This is a low-cost pricing option. See [Azure documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/spot-vms) for details. This does not affect the deployment of the virtual machine.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617746-2fd534e4-c76f-4968-9e58-21b58f0b11c3.PNG "Azure Spot discount option")

### Size

Select an appropriate [size](https://learn.microsoft.com/en-us/azure/virtual-machines/sizes) for your compute needs from the pull-down.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617748-5f17514b-5809-474c-b506-a9dec57448f5.PNG "Select an appropriate VM size")

## Administrator account

This section defines how users [connect](https://learn.microsoft.com/en-us/azure/virtual-machines/linux-vm-connect) to the VM instance.

### Authentication type (Linux systems)

 `SSH public key` is the most common and recommended choice.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617790-2493ec4d-0448-43cf-ae0a-39a405b863db.PNG "Select the 'SSH public key' authentication type")

 ### Username

 Create an appropriate username. The default username is `azureuser`. Windows VMs will also require a password to be set.

 ![alt-text #center](https://user-images.githubusercontent.com/67620689/235617796-f8112d4f-b16f-48f2-aa04-a27d8e3f1899.PNG "Set a username for the VM")

 ### SSH public key resource / Key pair name (Linux systems)

 Use an existing key pair or generate a new one, as defined by `Key pair name`. If `Generate new key pair` is selected, your private key will be generated during the [Create](#create-instance) step.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617798-5ed36a5c-1a0b-495c-ad54-eb81d650dea5.PNG "Select or create a key pair")

## Inbound port rules

These settings can be used to limit access to your VM. See the documentation for more info. This can generally be left as default. You can connect to Linux machines using SSH. You can connect to Windows machines using Remote Desktop Protocol (RDP).

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617801-055e0c32-6e0b-46be-9070-e6bcf9bed77f.PNG "Configure inbound ports if necessary")

## Licensing (Windows only)

Tick the box to confirm you have an appropriate license to deploy a Windows virtual machine. See the [Azure documentation](https://learn.microsoft.com/en-us/azure/virtual-machines/windows/windows-desktop-multitenant-hosting-deployment) for information.

## Other settings

There are other tabs defining many advanced settings. They can generally be left as default.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617807-c796c760-67c3-4a96-a7ed-ce2f95f2405b.PNG "Additional settings to configure the VM")

## Create instance

When the VM settings are to your liking, click on `Review + create`. Your settings will be validated by Azure. If valid, click on `Create` to create your VM instance.

![alt-text #center](https://user-images.githubusercontent.com/67620689/235617805-c622aa34-5abf-47ce-bd02-cd9c01b60957.PNG "Review and create the instance")

After a short time, the VM will be created. Click on `Go to resource` to see various parameters, particularly the `Public IP address`.

## Connect to your VM instance (Linux) {#linux}

These instructions are for Linux-based virtual machines. If you are using a Windows-based virtual machine, please jump to the [Windows section](#windows).

You can connect to the instance with your preferred SSH client. For example, if using the default username `azureuser`:

```console
ssh -i <private_key> azureuser@<public_ip_address>
```
You will also see this command under the `Connect` > `SSH` tab.

Terminal applications such as [PuTTY](https://www.putty.org/), [MobaXterm](https://mobaxterm.mobatek.net/) and similar can be used.

Once connected, you are now ready to use your instance.

## Explore your instance (Linux)

### Run uname

Use the [uname](https://en.wikipedia.org/wiki/Uname) utility to verify that you are using an Arm-based server. For example:

```console
uname -m
```
will identify the host machine as `aarch64`.

### Run hello world

Install the `gcc` compiler. If you are using `Ubuntu`, use the following commands. If not, refer to the [GNU compiler install guide](/install-guides/gcc):

```console
sudo apt-get update
sudo apt install -y gcc
```

Using a text editor of your choice, create a file named `hello.c` with the contents below:

```C
#include <stdio.h>
int main(){
    printf("hello world\n");
    return 0;
}
```
Build and run the application:

```console
gcc hello.c -o hello
./hello
```

The output is shown below:

```output
hello world
```

## Connect to your VM instance (Windows) {#windows}

These instructions are for Windows-based virtual machines. If you are using a Linux-based virtual machine, please jump to the [Linux section](#linux).

On your local host PC, launch the `Remote Desktop Connection` application.

Enter the `Public IP Address` of the Windows VM as the `Computer` to be connected to. Username can also be specified.

You will be prompted for the user password (set earlier), and you will connect. Once connected, you are now ready to use your instance. You can interact with the VM in the same way as you would a local desktop.

## Explore your instance (Windows)

Open `Control Panel` > `System` and verify that `Device` > `System Type` identifies as an Arm-based processor.
