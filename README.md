# Sitecore Forms
## XM Cloud Form setup
### Fields
As a bare minimum you need to compose your form of the following fields and make sure that the input field names match with the property names defined in the API request schema:
1.	**Guest Type**. This is a required property in the CDP that accepts one of the predefined values: _“visitor”_, _“customer”_ and _“traveller”_. For ease this can be configured as a hidden _Short Text_ field with a hardcoded “visitor” value and a _“guestType”_ name.
2.	**Name**. This is an optional property for a _Guest_, but important while building a _Customer_ profile. Use a _Short Text_ field with a _“firstName”_ name. In addition, you can also capture a surname by creating one more _Short Text_ field with _“lastName”_ name.
3.	**Email**, _email _

### Webhook
TBC
![Sitecore CDP webhook configuration](/assets/CDP-webhook-configuration.jpg)
