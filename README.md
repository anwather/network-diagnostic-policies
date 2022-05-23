# Networking Diagnostic Policies

## Project structure

- Policy definitions are stored in the ```policies\definitions``` folder.
- Policy initiatives are stored in the ```policies\initiatives``` folder.
- Assignments are stored in the ```policies\assignments``` folder. Policy assignments are an ARM template which also contains an RBAC resource.
- There are scripts to deploy the policy definitions and assignments.
- The ```globals.json``` file contains some global settings for deployment.

## Usage

1. Ensure the following software pre-requisites are available
    - PowerShell 7
    - PowerShell Az Modules
    - Bicep
2. Fill out the details in the ```globals.json``` file. The top level management group is the group which the policy definitions are deployed.
3. The policy initiatives need to have the management group name changed. Perform a search and replace on the files in ```policies\initiatives``` folder and replace ```contoso``` with your management group.
4. Rename the folder under the ```policies\assignments``` to match your management group e.g. rename the ```contoso``` folder.
5. Run the ```deploy-PolicyObjects.ps1``` script to deploy the policies. Note this may fail the first time due to a delay between the policy being deployed and being available to include in the initiative. If this happens simply run the script again.
6. Ensure that the details are completed for the parameter files in the ```policies\assignments``` folder. You will need to provide a Log Analytics workspace resource ID's and storage account ID's for NSG flow log policies. Examples are provided to make this policy work in Australia East and Australia Southeast - if other regions are required you will need to modify the initiative and assignment accordingly.
7. Run the ```deploy-policyAssignments.ps1``` script to deploy the policy assignments.