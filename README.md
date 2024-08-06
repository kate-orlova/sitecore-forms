[![GitHub license](https://img.shields.io/github/license/kate-orlova/sitecore-forms.svg)](https://github.com/kate-orlova/sitecore-forms/blob/master/LICENSE)
![GitHub language count](https://img.shields.io/github/languages/count/kate-orlova/sitecore-forms.svg?style=flat)
![GitHub top language](https://img.shields.io/github/languages/top/kate-orlova/sitecore-forms.svg?style=flat)
![GitHub repo size](https://img.shields.io/github/repo-size/kate-orlova/sitecore-forms.svg?style=flat)
![GitHub contributors](https://img.shields.io/github/contributors/kate-orlova/sitecore-forms)
![GitHub commit activity](https://img.shields.io/github/commit-activity/y/kate-orlova/sitecore-forms)

# Sitecore Forms
The Sitecore Forms project aims to accelerate your forms creation using the Sitecore XM Cloud Forms and connect them with the Sitecore CDP in two simple steps.

## XM Cloud Form setup
### Fields
As a bare minimum you need to compose your form of the following fields and make sure that the input field names match with the property names defined in the API request schema:
1.	**Guest Type**. This is a required property in the CDP that accepts one of the predefined values: _“visitor”_, _“customer”_ and _“traveller”_. For ease this can be configured as a hidden _Short Text_ field with a hardcoded “visitor” value and a _“guestType”_ name. ![Guest Type field configuration](/assets/Guest-Type-field.png)
2.	**Name**. This is an optional property for a _Guest_, but important while building a _Customer_ profile. Use a _Short Text_ field with a _“firstName”_ name. In addition, you can also capture a surname by creating one more _Short Text_ field with _“lastName”_ name. ![Name field configuration](/assets/Name-field.png)
3.	**Email**. This is an optional property, so capture it wisely if only you plan any email comms in future, for example, when a user is subscribing to a newsletter. Use an _Email_ field with _“email”_ name. ![Name field configuration](/assets/Email-field.png)

Of course, you can add as many fields as you wish to meet your specific requirements, there are no restrictions at all. Or, using a new and powerful “Add page” built-in functionality you can even create a multi-step form. So, Sitecore gives you the full freedom and you have the full control over your form composition including its look & feel.

### Webhook
XM Cloud Forms offer an easy way to send the submitted data to the third-party applications without capturing and storing the user data within the XM Cloud. Instead, the Forms use webhooks to send the data across the different touch points. 

So, to push your form submissions to the Sitecore CDP, create a webhook using the Guest REST API https://api-engage-eu.sitecorecloud.io/v2.1/guests with the basic authentication as a destination for your form submissions:

![Sitecore CDP webhook configuration](/assets/CDP-webhook-configuration.jpg)

For credentials use your **CDP Client Key** as a _username_ and your **CDP API Token** as a _password_, both values can be found in the _Management -> API Access_ section of your CDP app.

## Test Form Submission
You can test your form submission and check your webhook in action directly in the Forms app, go to the Settings section and click on the Test webhook button:
![Sitecore CDP webhook configuration](/assets/Test-webhook-action.png)

It will render your form as per your configuration and let you to fill it in with your test data, so that you can validate the data submission and see the exact payload that will be sent to your webhook.

The below is my payload example:

https://api-engage-eu.sitecorecloud.io/v2.1/guests

```
{
    "guestType": "visitor",
    "firstName": "Kate",
    "lastName": "Orlova",
    "email": "kate.orlova+30072024@unrvld.com",
    "test": true
}
```
These are the request headers that will be sent:
```
{
  "Date": "<timestamp when the data was submitted>",
  "X-Forwarded-For": "<the address of the end user, if available>",
  "User-Agent": "<browser where the data was submitted from, if available>",
  "Referer": "<request referrer, if available>",
  "X-FormId": "<form id>",
  "X-FormName": "<form name>"
}
```

