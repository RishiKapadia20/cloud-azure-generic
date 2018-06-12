
# Azure - Generic Opspack

Microsoft Azure is a cloud computing service created for building, testing, deploying, and managing applications and services through a global network of Microsoft-managed data centers. It provides software as a service (SAAS), platform as a service and infrastructure as a service and supports many different programming languages, tools and frameworks, including both Microsoft-specific and third-party software and systems.

## What You Can Monitor

Opsview Monitor's Azure Generic Opspack provides all the metrics to track your custom metrics. Easily integrate your custom defined Azure metrics within a few clicks.


## Service Checks

| Service Check |
|:------------- |
|Azure-Redis-Generic: Metric Name 1
|Azure-Redis-Generic: Metric Name 2

## Prerequisites

The monitoring plugin for this Opspack has been tested with Python 2.7. In order for the Opspack to run, you will need to have some Python packages installed by running the pip python package tool.

If a cryptography error occurs when trying to install the Azure packages, you can run the commands which should fix the problem.

**Debian and Ubuntu**

```sudo apt-get install build-essential libssl-dev libffi-dev python-dev python-pip```

**CentOS and RHEL**

```sudo yum install gcc libffi-devel python-devel openssl-devel python-pip```

**Common**

When python-pip is installed, you can then run:
```
sudo pip install --upgrade pip==9.0.2
sudo pip install --upgrade setuptools
sudo pip install --upgrade requests
sudo pip install nagiosplugin
sudo pip install azure
sudo pip install azure-monitor
```

## Setup Azure for Monitoring

To monitor you Azure environment, you need to configure it for monitoring

This requires Administrator access on Azure. You need to retrieve the following credentials:

* Subscription ID
* Tenant/Directory ID
* Client/Application ID
* Secret Key

#### Step 1: Find Subscription ID

The Subscription ID can be found in the **Subscriptions** section under the **All services** section from the Azure dashboard

![Find Azure Subscription ID](/docs/img/azure_find_subscription_id_1.jpg?raw=true)

![Find Azure Subscription ID](/docs/img/azure_find_subscription_id_2.jpg?raw=true)

#### Step 2 : Find the Tenant/Directory ID

The Tenant/Directory ID can be found in the **Azure Active Directory** under the **Properties** section from the Azure dashboard

![Find Azure Tenant/Directory ID](/docs/img/azure_find_directory_id.png?raw=true)

#### Step 3: Find the Client/Application ID for your application

You need to create and register your application if you haven't already. Use the following documentation from Microsoft: [Create an Azure Active Directory application](
https://docs.microsoft.com/en-us/azure/azure-resource-manager/resource-group-create-service-principal-portal#create-an-azure-active-directory-application)

The Client/Application ID can be found in **Azure Active Directory** under the **App registrations** section from the Azure dashboard

![Find Azure Client/Application ID](/docs/img/azure_find_application_id.png?raw=true)

#### Step 4: Generate the Secret Key for your application

You will need to create a Secret Key for your application, once this has been created its value will be hidden so save the value during creation

To create the Secret Key, select your application from the list, select the **Settings** within your application and then select the **Keys** option

There you can create a new key by adding the description and expiration period and the value will be generated

![Create Secret Key](/docs/img/azure_create_secret_key.png?raw=true)

#### Step 5: Provide access to the subscription you wish to monitor

Navigate to the **Subscriptions** section and select the Subscription you selected before

In the Subscription to be monitored, click **Access Control (IAM)**

Then click the **Add** button, select **Reader** and select the application

![Add Subscription to Application](/docs/img/azure_add_subscription_1.png?raw=true)

![Add Subscription to Application](/docs/img/azure_add_subscription_2.png?raw=true)

If you are running more than one subscription these steps will need to be done for each one you wish to monitor

## Setup and Configuration

To configure and utilize this Opspack, you simply need to add the 'Cloud - Azure - Virtual Machines' Opspack to your Opsview Monitor system

#### Step 1: Add the host template

![Add Host Template](/docs/img/host-template.png?raw=true)

#### Step 2: Add and configure variables required for this host

Add 'AZURE_CREDENTIALS' to the host and set the **Resource Group** as its variable value

Then override the Subscription ID, Client ID, Secret Key and Tenant ID

![Add Variables](/docs/img/variable.png?raw=true)

#### Step 3: Reload and the system will now be monitored

![View Output](/docs/img/output.png?raw=true)
