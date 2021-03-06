---
layout: single
title: "vRealize Automation Lab Manual"
date: 2018-07-20
tags: workshop
toc: true
classes: wide
author_profile: false
comments: true
---
# Introduction

Very often, customers want to utilise tools which sit above the vCenter API layer and provide additional value to the consumption or monitoring process. One such tool is VMware vRealize Automation which can be utilised to create a governance and "store front" portal so that users can provision workloads where they wish, based on policies defined by the Cloud Administrator.

## What is vRealize Automation (vRA)

VMware vRealize Automation is the IT Automation tool of the modern Software-Define Data Center. vRealize Automation enables IT Automation through the creation and management of personalized infrastructure, application and custom IT services (XaaS). This IT Automation lets you deploy IT services rapidly across a multi-vendor, multi-cloud infrastructure.

• Agility Through IT Automation

  Accelerate the end-to-end delivery and management of infrastructure and applications.

• Choice Through Flexibility

  Provision and manage multi-vendor, multi-cloud infrastructure and applications by leveraging new and existing infrastructure, tools and processes.

• Control Through Governance PoliciesControl Through Governance Policies

  Ensure that users receive the right size resources, or applications, at the appropriate service level for the jobs they need to perform.

• Cost Saving Through Efficiency

  Cost Saving Through Efficiency Reduce operational cost by replacing time-consuming, manual processes and gain additional cost savings through automated reclamation of inactive resources.

vRealize Automation supports VMware Cloud on AWS in delivering a unified hybrid cloud management experience.

## Login to vRealize Automation

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA1.jpg)

1\. On your Student desktop, click on the Chrome browser.

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA2.jpg)

2\. On your bookmarks bar in Chrome click on the *VMware vRealize Automation Appliance* link

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA3.jpg)

3\. Click on the *Proceed to vraapp.corp.local (unsafe)* link

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA4.jpg)

5\. Click on the *vRealize Automation Console* link

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA5.jpg)

6\. Click *Next*

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA6.jpg)

7\. Login with your *vmcws#* user name (where # is your student number)

8\. Enter your password - **VMware1!**

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA7.jpg)

You have successfully logged in to vRealize Automation!

## Add a vSphere Endpoint

An endpoint is anything that vRealize Automation uses to complete it's provisioning processes. This could be a public cloud resource such as Amazon Web Services EC2, Microsoft Azure, VMware Cloud on AWS, an external orchestrator appliance, or a private cloud hosted by vSphere or other hypervisors.

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA8.jpg)

1\. Click on the *Infrastructure* tab

2\. Click on *Endpoints* on left pane

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA9.jpg)

3\. Click on *Endpoints* again on the left pane

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA10.jpg)

4\. Click on *New* button

5\. Select *Virtual*

6\. Select *vSphere (vCenter)*

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA11.jpg)

For these next few steps, make sure you are logged in to your VMware Cloud on AWS portal.

7\. On your VMware Cloud on AWS portal, make sure you click on the *Settings* tab, you will be using some of this information to create the vRealize Automation Endpoint

8\. Name your vRA Endpoint **ws#** (where # is your student number)

9\. Under *Address* enter the information from the VMware Cloud on AWS portal under *vSphere Client (HTML5)* and replace the words 'ui' for 'sdk'

10\. Example:

From VMware Cloud on AWS portal: <https://vcenter.sddc-X-X-X-X.vmc.vmware.com/ui>

  What it should look like in vRealize Automation: <https://vcenter.sddc-X-X-X-X.vmc.vmware.com/sdk>

11\. Enter the user name **cloudadmin@vmc.local**

12\. Enter the password (Please refer to VMware Cloud on AWS portal for this information)

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA12.jpg)

13\. Click on the *Test Connection* button

14\. If connection passes test, click on *Ok* button to create your vRealize Automation Endpoint

## Create a Fabric Group

An administrator can organize virtualization compute resources and cloud endpoints into fabric groups by type and intent. Make sure for this step you've selected the Endpoint you created in the previous module.

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA13.jpg)

1\. Click on *Fabric Groups* on the left pane

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA14.jpg)

2\. Click on *+ New* to create a new Fabric Group

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA15.jpg)

3\. Name your Fabric Group **ws#FabricGroup** (where # is your student #)

4\. Add the user assigned to your student number: *vmcws#@corp.local* and click on the magnifying glass icon to find and add your user

5\. Select the vRealize Automation endpoint you created in the previous step

*NOTE*: MAKE SURE YOU SELECT THE CORRECT COMPUTE RESOURCE AS ILLUSTRATED BY THE ARROWS. SHOULD BE THE "WS#" ENDPOINT YOU CREATED IN A PREVIOUS STEP.

6\. Click *OK* button

## Reservations

When a user requests a machine, it can be provisioned on any reservation of the appropriate type that has sufficient capacity for the machine. You can apply a reservation policy to a blueprint to restrict the machines provisioned from a that blueprint to a subset of available

### Create Reservation Policy

For this step if your Reservation tab is missing you may need to hit the Refresh button on your browser.

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA16.jpg)

1\. Click on the *Infrastructure* button on the left pane

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA17.jpg)

2\. Click *Reservations* on the left pane

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA18.jpg)

3\. Click *Reservation Policies* on the left pane

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA19.jpg)

1\. Click *New* button

2\. Name your Reservation Policy *Student#*

3\. Click *OK* button

### Create a Reservation

A vRealize Automation reservation is a means to allocate resources in a fabric group (CPU, RAM, Storage, etc.) to a specific business group.

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA20.jpg)

1\. Click on the *Infrastructure* button on the left pane

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA21.jpg)

2\. Click on *Reservations* on the left pane

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA22.jpg)

3\. Click *Reservations* on the left pane

4\. Click *+ New* to create a new Reservation

5\. Select *vSphere (vCenter)*

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA23.jpg)

6\. Give your reservation a name: **Student#** (where # is your student number assigned to you)

7\. Leave/select *vsphere.local* as the Tenant

8\. Select *vmc-ws#* (where # is your student number)

9\. For Reservation policy type or select *Student#* (where # is your student number assigned to you)

10\. Priority should be set to *1*

11\. Click on the *Resources* tab

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA24.jpg)

12\. On the *Resources* tab for *Compute Resource* select *Cluster-1 (WS#)* from the drop down box

13\. Type **1024** in the *This Reservation* field

14\. Select the checkbox for *WorkloadDatastore*

15\. Type **10000** under the *This Reservation Reserved* field

16\. Type **0** under the Priority field and hit the *OK* button

17\. Select *Compute-ResourcePool* in the *Resource Pool* field

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA25.jpg)

18\. Click on the *Network* tab

19\. Select the *sddc-cgw-network-1* Network Adapter by clicking the checkbox to the left of it and selecting *sddc-cgw-network-1* from the dropdown box on the right side

20\. Click on the *OK* button

## Create a Blueprint

A blueprint is a complete specification for a service. A blueprint determines the components of a service, which are the input parameters, submission and read-only forms, sequence of actions and provisioning. You can create service blueprints to provision custom resources that you previously created.

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA26.jpg)

1\. Click on the *Design* tab

2\. On the left pane click *Blueprints*

3\. Click the *+ New* button

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA27.jpg)

4\. Name your Blueprint **Student#** (where # is the Student number assigned to you)

5\. Use the same name for ID

6\. Enter **1** as the Deployment Limit

7\. Enter **1** as the Minimum Lease days

8\. Enter **1** as the Maximum Lease days

9\. Enter **0** for Archive Days

10\. Click the *OK* button, the Design Canvas below appears

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA28.jpg)

11\. Ensure *Machine Types* is selected

12\. Click and drag onto the Canvas the *vSphere (vCenter) Machine*

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA29.jpg)

13\. Leave all defaults on the *General* tab and click on the *Build Information* tab

14\. Make sure *Server* is selected as the Blueprint Type

15\. Change Action to *Clone*

16\. Click on the elipsis button and select *StudentVM#* that you created in your previous step and click *OK*

17\. Click *Save*

18\. Click *Finish*

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA30.jpg)

19\. Select your Blueprint by highlighting it

20\. Click on the *Publish* button to publish your blueprint

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA31.jpg)

21\. Make sure you are in the *Administration* tab, if not, click on it and select *Catalog Management*

22\. Select *Catalog Items* from the left pane and click your *Student#* to configure

23\. Select *Desktops* from the drop down box next to *Service*

24\. Click the *OK* button

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA32.jpg)

### Entitle your Blueprint

25\. Click the *Administration* tab

26\. Select *Catalog Management* from the left pane

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA33.jpg)

27\. Click on *Entitlements* on the left pane

28\. Click the *+ New* button in order to create a new Entitlement

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA34.jpg)

29\. Name the Entitlement **ws#** (where # is your Student #)

30\. Change the Status to *Active*

31\. Select *vmc-ws#* for the Business Group (where # is the number assigned to you)

32\. Click *Next*

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA35.jpg)

33\. Click the *+* sign next to *Entitled Services*

34\. Make sure to select the checkbox next to *Desktops*

35\. Click *OK*

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA36.jpg)

36\. Click on the *+* sign next to *Entitle Actions*

37\. Select the checkbox at the top to select all Actions

38\. Click *OK* button

39\. Click *Finish* button

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA37.jpg)

### Request a catalog item

40\. Select the *Catalog* tab

41\. Click on your newly created *Student#* blueprint and click on the *Request* button

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA38.jpg)

42\. Highlight the *vSphere_VCenter_Machine* under your Blueprint

43\. Check all the options are correct and click the *Submit* button

![](https://s3-us-west-2.amazonaws.com/vmc-workshops-images/vra/vRA39.jpg)

44\. Click on the *Requests* tab to check on the status of your Blueprint submission

45\. Check the status to ensure the request completes successfully
