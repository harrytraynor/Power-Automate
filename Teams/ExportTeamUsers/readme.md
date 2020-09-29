# Export Details about Team Members

This will run on a schedule, which is recommended at intervals of 15 minutes. It will pull all the information regarding team users into a SharePoint list for auditing or admin purposes. Getting insights into who you users are and what their job roles are can be useful.

This Flow will update the teams details if they already exist in the list, and remove them if they are no longer part of the team.

## Import Flow

Please refer to the guide [here](https://flow.microsoft.com/en-us/blog/import-export-bap-packages/#:~:text=Importing%20a%20flow%201%20To%20import%20a%20flow%2C,flow%20definition%20from%20the%20package%20More%20items...%20) to import the Flow into Power Automate.

### Connectors Required

- SharePoint
- Office 365 Users

## Prepare Flow

- Update "Tenant ID", "Client ID", and "Secret" variables with the ones found in your [Azure AD Application](https://github.com/harrytraynor/Power-Automate/blob/master/setupazureapp.md).
- Create a SharePoint list where you want all the basic details of the team users to be stored. It will need at least a "Email", and "Department", "Office", and "Job title".
- Update all the mentioned of SharePoint actions in the Flow to have the link of your newly created list.

## Running the Flow

Open [flow.microsoft.com](https://flow.microsoft.com) and as long as the Flow has been enabled it will trigger on the schedule you have defined. The more often you run this the more up to date the list will be when new team members join or leave. This has some uses but be careful not to exceed the limitations / rate limits that Office 365 set.

## Troubleshooting

- Ensure all your details from the Azure AD Application are correct.
- Ensure you have entered all the columns required in the SharePoint list.
