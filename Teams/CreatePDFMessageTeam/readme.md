# Create a PDF and Post to a Teams Channel

This will trigger from any file being placed in a OneDrive folder, convert it to a PDF, and ask the owner where they would like to place the output through a Teams chat message. Once Selected the Flow will move the file to the SharePoint folder of the selected channel and post a share link into the channel also.

## Import Flow

Please refer to the guide [here](https://flow.microsoft.com/en-us/blog/import-export-bap-packages/#:~:text=Importing%20a%20flow%201%20To%20import%20a%20flow%2C,flow%20definition%20from%20the%20package%20More%20items...%20) to import the Flow into Power Automate.

### Connectors Required

- Office 365 Users
- OneDrive for Business
- SharePoint

## Prepare Flow

- Update the OneDrive ation called "When file created in Attachments" with the folder you want to be monitored for any new files being added.
- Update "Team Name" variable with the exact name of the team you want to work with. Spaces allowed.
- Update "Team Name SharePoint" with the url part of your team's SharePoint. `https://<tenant>.sharepoint.com/sites/<team_name_sharepoint>`. This is only if you have changed the name of your team since its creation, otherwise duplicate the value from the previous step.
- Please note the other three variables should be empty.
- Update the "Approval from User" action with the message you would like to ask your end user. This is where the choices will be presented. This used Adaptive Cards to display the data to the end user, so please make sure to use this [link](https://adaptivecards.io/designer/) to change any data.
- Update the tenant address for the SharePoint actions near the bottom of the Flow.These are called "Create a File", and "Create a share link for a file or folder". The start part needs the `https://htd3v.sharepoint.com/sites/` changed to `https://<tenant>.sharepoint.com/sites/`.
- Finally update the last action in the Flow "Post a message as the Flow bot to a channel" to include the share link and anything else you would like to post.

## Running the Flow

Open [flow.microsoft.com](https://flow.microsoft.com) and as long as the Flow has been enabled it will trigger when a new file is added to the configured folder. The user will then be notified through Teams as to where they would like the new file posted.

## Troubleshooting

- Please not that the file types that this Flow can convert to PDF are limited. In testing all the normal Office document types work fine.
- When editing the adaptive card please ensure that the version of the header is seet to `"version": "1.0"` as this can be chnaged automatically by using the online editor.
- There can be cases where if the file name already exists in the SharePoint sturcture, the Flow will not overwrite it and will fail to run.
