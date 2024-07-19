# User and Team

## Team Overview

<figure><img src="../../.gitbook/assets/image (8).png" alt=""><figcaption></figcaption></figure>

## User

Currently, ReByte support the following login methods:

* Email
* Google
* Github

ReByte uses email as the primary identifier for a user. Notably, GitHub does not provide **verifed email**, so if you log in with GitHub, you will be asked to provide an email address.

## Team

Team is a concept that allows multiple users in same organization to collaborate on the same knowledge/agent/assistant, also enforce access control. Team can have multiple members, and each member can have different access level. Each login user has one default team, named after the user's display name, for example, if your display name is "John Smith", then your default team name will be "John Smith's Personal Team".

For example, if you are a developer in a company, you can create a team called "ACME" and invite your colleagues to join the team. Then you can create knowledge and agent under the team, and all your colleagues can access the knowledge and agent.

* User can belong to multiple teams, he can change his default team in the team switcher in upper left corner of the UI.
* Each team has its own API Key, which can be used to access all tools and knowledge that belongs to the team.
* Team has a unique ID to identify the team, you can find the team ID in the team settings page. Team ID is particularly useful when you want to use ReByte via SDK.

#### Role

Each member in a team has a role, which determines the access level of the member. There are 4 roles in a team:

* **Owner**: User who sets up the team is the owner of the team, he has full access to the team, he can invite new members, change team settings, and access all tools and knowledge in the team.
* **Admin**: Owner has full access to the team, he can invite new members, change team settings, and access all tools and knowledge in the team.
* **Builder**: Builder can access create tools/knowledge/assistants in the team, but builder cannot change team settings or invite new members.
* **User**: User can access assistant created by the team, User can also contribute knowledge to shared knowledge base. Other than that, User cannot access tools or change team settings.

[//]: # (see also: [Access Control]&#40;access-control.md&#41; for more details.)
