# Request Team - Approval

This will trigger whenever a Form response is submitted. This Form could be embedded into a Teams app and pushed onto the side rail of Teams for easy access. It will then take the output of the Form, start an approval with the "New Teams Approvers" group, and log this to a SharePoint list fot auditing purposes.

## Import Flow

Please refer to the guide [here](https://flow.microsoft.com/en-us/blog/import-export-bap-packages/#:~:text=Importing%20a%20flow%201%20To%20import%20a%20flow%2C,flow%20definition%20from%20the%20package%20More%20items...%20) to import the Flow into Power Automate.

### Connectors Required

- Microsoft Forms
- SharePoint
- Microsoft Teams
- Azure AD
- Approvals

## Prepare Flow

- Create a new Form using [forms.office.com](https://forms.office.com). It will need at least a "Team Name", and "Team Description" field to populate the new team details.
- Update "When a new response is submitted" to the correct Form created in the last step.
- Update "Get response details" with the correct Form name.
- Leave "Group Member Emails" variable blank.
- Update "Get group members" with the Object ID found in Azure AD or Office Admin Portal. More details [here](https://docs.microsoft.com/en-us/azure/active-directory/fundamentals/active-directory-groups-view-azure-portal) when using Azure AD.
- Update "Start and wait for an approval" with the Form fields you chose to use, and any custom message you would prefer. Make sure this is also configured to how you want to request pattern to occur e.g. `Approve/Reject - First to respond`.
- Expand the "Condition" action and update the following:
  - Update "Create a team" with the correct fields from the Form.
  - Update "Ping message to requester about Team creation" to include the fields from the Form if you so wish, and or customise the message the user gets when successfully creating the team.
  - Update "Ping message to requester about approval denied" to include the fields from the Form if you so wish, and or customise the message the user gets when the approval is denied.
  - *(optional)* Create a SharePoint list where you want all the basic details of the create teams to be logged. It will need at least a "Team Name", and "Team Description" column.
  - *(optional)* Update "Log in SP list" with the previous steps SharePoint list details.

## Running the Flow

Open [flow.microsoft.com](https://flow.microsoft.com) and as long as the Flow has been enabled it will trigger when a new response is submitted to the Form you created earlier.

## Troubleshooting

- Please ensure the Form has been created with the correct fields to make this Flow run.
- Make sure you have the correct permissions to poll with Azure AD.
- Make sure you have the right Object ID for the group you want to use.
