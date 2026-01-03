---
title: Rocket.Chat Tricks
site: tricks
type: tricks
---

#### Unconvert Team back to the Channel in Rocket.Chat

You might be already trying this little “Convert to Team” button located under “Channel > Information > ⋮” menu. It works, BUT:

**There is no way to undo this action via Rocket.Chat UI! 😡**

Lucky us, it’s possible via API:

1. Get your \`userId\` and \`authToken\` using [/api/v1/login](https://developer.rocket.chat/reference/api/rest-api/endpoints/other-important-endpoints/authentication-endpoints/login).
2. Find your \`teamId\` via [/api/v1/teams.listAll](https://developer.rocket.chat/reference/api/rest-api/endpoints/team-collaboration-endpoints/teams-endpoints/list-all-teams-with-info).
3. Finally, convert your team back to the channel calling [/api/v1/teams.convertToChannel](https://developer.rocket.chat/reference/api/rest-api/endpoints/team-collaboration-endpoints/teams-endpoints/convert-team-to-channel).

**Done! 🎉**

Never give up! And always check API docs 🤖
