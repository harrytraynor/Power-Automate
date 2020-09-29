# Mass Email from CSV

This takes a CSV from the users OneDrive and emails all of the users from it. A formatted CSV can be found in the repository as an example.

## Import Flow

Please refer to the guide [here](https://flow.microsoft.com/en-us/blog/import-export-bap-packages/#:~:text=Importing%20a%20flow%201%20To%20import%20a%20flow%2C,flow%20definition%20from%20the%20package%20More%20items...%20) to import the Flow into Power Automate. This is a basic Flow that uses OneDrive and Outlook connectors.

## Prepare Flow

- Import CSV to a OneDrive folder of your choice.
- Update "Get Emails From CSV" OneDrive action in the Flow to the folder you have chosen.
- Update "Send From Email" variable to the email address you want this to come from. This must be the email you are using or one you have full delegated access to.
- Expand all the elements actions on the Flow to reveal the "Send an email (V2)", where you can customise the message and subject line of the email.

## Running the Flow

Open [flow.microsoft.com](https://flow.microsoft.com) and trigger the flow by pressing play on it. As long as everything has been configured correctly in the pervious step it should run.

## Troubleshooting

- Double check you have permission to the email account you have chosen to send email from.
- Make sure you have selected the correct file from the OneDrive file selector.
- The average time to send around 5000 emails is ~25 minutes. Please bear that in mind when sending large campaigns.
- Ensure the first line of the CSV is an email, and there are no headings in the list. Otherwise it will try and email it and error.
- For the sake of speed the Flow does not check every email address it is sending. It will error if it cannot send one, btu will continue with the rest of the CSV regardless.
