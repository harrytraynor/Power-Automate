# Create Team - Automatic

This will run on a schedule, which is recommended at intervals of 15 minutes. It will pull all the information regarding Teams into a SharePoint list for auditing or admin purposes. This can also be a more efficient way of polling your tenant for a list of all available teams without having to use Microsoft Graph.

This Flow will update the teams details if they already exist in the list, and update any information like how many owners there are. This could be used to automatically send messages to teams who don't meet the minimum required amount of owners for a team.

## Import Flow

Please refer to the guide [here](https://flow.microsoft.com/en-us/blog/import-export-bap-packages/#:~:text=Importing%20a%20flow%201%20To%20import%20a%20flow%2C,flow%20definition%20from%20the%20package%20More%20items...%20) to import the Flow into Power Automate.

### Connectors Required

- SharePoint
- Microsoft Teams

## Prepare Flow

- Update "Tenant ID", "Client ID", and "Secret" variables with the ones found in your [Azure AD Application](https://github.com/harrytraynor/Power-Automate/blob/master/setupazureapp.md).
- Create a SharePoint list where you want all the basic details of the team to be stored. It will need at least a "Team Name", and "Team Description", "Team ID", "Owner", "Member Count", "Owner Count", and "Team Visibility".
- Update all the mentioned of SharePoint actions in the Flow to have the link of your newly created list.

## Running the Flow

Open [flow.microsoft.com](https://flow.microsoft.com) and as long as the Flow has been enabled it will trigger on the schedule you have defined. The more often you run this the more up to date the list will be when new teams are generated. This has some uses but be careful not to exceed the limitations / rate limits that Office 365 set.

## Troubleshooting

- Ensure all your details from the Azure AD Application are correct.
- Ensure you have entered all the columns required in the SharePoint list.
