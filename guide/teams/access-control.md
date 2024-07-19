# Access Control

ReByte is built with fine-grained access control. You can control the visibility of your tools, knowledge, assistant and other resources in ReByte. We believe that this is of vital importance for collaboration and sharing AI applications in enterprise environments.

## Rules

There are three types of users regarding access control:

* **Builders** (builder/admin/owner of a team): develop and maintain the team's tools, knowledge, and apps.

* **Users**: use assistants created by the team.

* **External Users**: ReByte users who are not part of the team.

Builders can develop, design, and use the tools, knowledge, and assistants within the team. Users can view and use the assistants created by the team. External users can view and use the tools, knowledge, and apps that are set to External Public.

Regarding tools, users can view all tools' workflows and datasets within the team and can copy them to their personal accounts to modify and run. When an agent is set to External Unlisted, users outside the team can use a link to view the agent. When an agent is set to Public, it appears in the team agent list for external users.

Regarding knowledge, it can be set so only admins and owners can create knowledge, while builders can maintain it. External Public set knowledge can be viewed by users outside the team.

Regarding apps, there are four access-levels. Private apps can only be seen by builders, which is useful for maintaining apps that are still under development.team Unlisted apps can be accessed and used by team users via a link. Apps set to Team Public can be viewed and used by all team members on the team app page. External Public means that users outside the team can also view and use the app.

For example, in an administrative team, the owner and admin manage the team's resources, builders are responsible for designing and building tools, knowledge, and apps. And users are responsible for viewing and using the tools, knowledge, and apps designed by the builders. When an app is not yet complete, a builder can set its access-level to Private. Once the design is finished, it can be set to Team Public for team members to use. Setting it to External Public allows sharing with users outside the team.

Further details are available in the following table:

| Team-Access       | Non-team user        | Team user（member）               | Team Builder（admin、owner）      |      |
| ----------------- | -------------------- | --------------------------------- | --------------------------------- | ---- |
| Team-App          |                      |                                   |                                   |      |
| Private           |                      |                                   | list,use,edit,create              |      |
| team Unlisted     |                      | Use with link                     | list,use,edit,create              |      |
| team Public       |                      | list,use                          | list,use,edit,create              |      |
| External Public   | list,use             | list,use                          | list,use,edit,create              |      |
| Team-Knowledge    |                      |                                   |                                   |      |
| External Public   | list,use             | list,use                          | list,use,edit,create(admin&owner) |      |
| team Public       |                      | list,use                          | list,use,edit,create(admin&owner) |      |
| Team-Tool        |                      |                                   |                                   |      |
| team Public       |                      | list,view（design,dataset）,clone | list,view,edit,create             |      |
| External Unlisted | view,clone with link | list,view,clone                   | list,view,edit,create             |      |
| External Public   | list,view,clone      | list,view,clone                   | list,view,edit,create             |      |
