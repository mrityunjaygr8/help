<meta name="robots" content="noindex">

# Deploy Spot PC Workflow
Deploying Spot PC desktops with Spot PC takes two simple configuration workflows: [Create Image](spot-pc/tutorials/deploy-spot-pc?id=create-image) and [Create Spot Group](spot-pc/tutorials/deploy-spot-pc?id=create-spot-group)

NOTE: This is the Spot PC workflow, for Windows 365 Cloud PC, [click here](spot-pc/tutorials/deploy-windows-365-cloud-pc).

# Create Image

Creating a VM image is the first step towards adding a new (or additional) group of users and resources to an organization.  The image will then be assigned to the Spot Group created in the [next step](spot-pc/tutorials/deploy-spot-pc?id=create-spot-group) of this process.

VM images for Spot PC are contained within Image Sets. Each new iteration of an image is represented within Spot PC as an Image with an incremented version number, all contained within a single Image Set. Then, an Image Set is assigned to a Spot Group, linking that image (and version) to that Spot Group. With this linkage intact, Spot PC optimization can automation the creation, deletion and availability of Spot PC session hosts for end users in real-time. Rolling out changes to the session host(s) is also simplified, once the new image version is created and tested, the Spot Group can be linked with the new image version and automation handles a seamless cutover to the new image.

## Creating a New Image Set

New image sets can be created based off of an Azure Marketplace Image.

To begin the process of creating a new Image Set and Image version 0.0.0:

- Navigate to the desired tenant
- Open the _Config Actions_ menu, open _Images_ and select _Create_
- The _New Image Set_ workflow has four steps

### Select Site

Select the site for the VM Image to be built (and to reside in) once completed You can select from all available sites in the tenant or a _Global_ option.

The _Global_ option will add the image to the Azure Shared Image Gallery and replicate the image across multiple Azure regions. <br>
NOTE: Due to replication time, the global image set won't be immediately available for customization. Please expect approximately 20 minutes of delay once the global image is saved.

### Select Image Source

The drop down for _Image Source_ is populated from Azure Marketplace, with filters applied to narrow the list to images relevant to Spot PC.

Depending on your use case, select the appropriate version of Windows.
If unsure, Spot PC recommends:

Pooled Spot Group
* office-365-21h1-evd-o365pp
* office365-win11-21h2-avd-m365
* windows-10-s1h1-evd

Personal Spot Group
* windows-10-21-h1-ent

### Image Name and Description

Enter a name and description for this Image Set. Choose the name and description that will help you find and organize Image sets.

The description can be edited later if needed.

### Add Notes and Save

Review your selections, navigate to _previous_ steps to make changes.

Add notes to document any important information about this image set and the 0.0.0 version. The goal is to write down how and why changes are being made for reference later by you or your colleagues.

## Creating a New Image Version

A new version of an existing image can be created from with an Image Set.

To begin the process of creating a new Image version:

- Navigate to the desired tenant
- Open the _Config Actions_ menu, open _Images_ and select _List_
- Click to open the desired Image Set
- Click _+ Add New Version"
- The _New Image Set_ workflow has five steps

Follow the workflow covering the same data as the [Creating a New Image Set](spot-pc/tutorials/deploy-spot-pc?id=creating-a-new-image-set) workflow above but entering an incremented version number.

# Create Spot Group
## Create Spot Group Workflow
Creating a Spot group is the second step towards adding a new (or additional) group of users and resources to an organization.  The image created in the [first step](spot-pc/tutorials/deploy-spot-pc?id=create-image) of this process will be used.

Creating a Spot Group can be done from the _Config Actions_ menu, found when inside any tenant.
<br><a href="https://docs.spot.io/spot-pc/_media/tutorials-create-spot-group-01.png" target="_blank"><img src="/spot-pc/_media/tutorials-create-spot-group-01.png" alt="Click to Enlarge" width="500"> </a>

Clicking _Create_ will open the Create Spot Group workflow is displayed.

## Create Spot Group

### Enter Spot Group Name  
Enter a name and friendly name for the Spot Group.

### Enter Profile Path
Enter the path to the data volume that will host the company shared data and the users' personal data.

### Select Spot Group License
Select the type of user licensing to be used for this Spot Group.

Pooled users share a session host which personal users a dedicated session host when connecting. All users in a Spot Group must be the same user type.

Use the slider to define the total number of named licenses you with to assign to this Spot Group.  This should equal the total number of users you'll have accessing resources in this Spot Group.

### Select Site
Select the site into which you wish to deploy this Spot Group.

### Select Groups
Select the existing AD Security Group(s) which contain the users to be assigned to this spot group.  

### Select Image Set
Select the image set and image version that will be used to build session hosts for this Spot Group.

### Description
Enter a useful description of this Spot Group to help you and other Spot PC Admins identify this Spot Group, who it is for, and how it is unique.

Add notes to document any important information about this new image version. The goal is to write down how and why changes are being made for reference later by you or your colleagues.

### Review and Save Spot Group
Review your selections, navigate to _previous_ steps to make changes.

Once saved, the Spot PC automation engine will build and configure the environment to support this new Spot Group, the users and the session hosts.


## What’s Next?

Learn more about [Connecting to the Spot PC desktop](spot-pc/tutorials/connect-to-desktop) as an end user.
