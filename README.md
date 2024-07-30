[![GitHub license](https://img.shields.io/github/license/kate-orlova/sitecore-forms.svg)](https://github.com/kate-orlova/sitecore-forms/blob/master/LICENSE)
![GitHub language count](https://img.shields.io/github/languages/count/kate-orlova/sitecore-forms.svg?style=flat)
![GitHub top language](https://img.shields.io/github/languages/top/kate-orlova/sitecore-forms.svg?style=flat)
![GitHub repo size](https://img.shields.io/github/repo-size/kate-orlova/sitecore-forms.svg?style=flat)
![GitHub contributors](https://img.shields.io/github/contributors/kate-orlova/sitecore-forms)
![GitHub commit activity](https://img.shields.io/github/commit-activity/y/kate-orlova/sitecore-forms)

# Sitecore Forms
## XM Cloud Form setup
### Fields
As a bare minimum you need to compose your form of the following fields and make sure that the input field names match with the property names defined in the API request schema:
1.	**Guest Type**. This is a required property in the CDP that accepts one of the predefined values: _“visitor”_, _“customer”_ and _“traveller”_. For ease this can be configured as a hidden _Short Text_ field with a hardcoded “visitor” value and a _“guestType”_ name. ![Guest Type field configuration](/assets/Guest-Type-field.png)
2.	**Name**. This is an optional property for a _Guest_, but important while building a _Customer_ profile. Use a _Short Text_ field with a _“firstName”_ name. In addition, you can also capture a surname by creating one more _Short Text_ field with _“lastName”_ name. ![Name field configuration](/assets/Name-field.png)
3.	**Email**. This is an optional property, so capture it wisely if only you plan any email comms in future, for example, when a user is subscribing to a newsletter. Use an _Email_ field with _“email”_ name. ![Name field configuration](/assets/Email-field.png)


### Webhook
Create a webhook using the Guest REST API https://api-engage-eu.sitecorecloud.io/v2.1/guests with the basic authentication as a destination for your form submissions:

![Sitecore CDP webhook configuration](/assets/CDP-webhook-configuration.jpg)

For credentials use your **CDP Client Key** as a _username_ and your **CDP API Token** as a _password_, both values can be found in the _Management -> API Access_ section of your CDP app.

##Test Form Submission
You can test your form submission and check your webhook in action directly in the Forms app, go to the Settings section and click on the Test webhook button:
![Sitecore CDP webhook configuration](/assets/Test-webhook-action.png)
