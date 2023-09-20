# KeyMaker Project presentation

The KeyMaker initiative strives to provide the tools unlocking the potential for participation and contribution in decentralized autonomous organizations (DAOs) by streamlining associated processes.

It is modeled after the Keymaker character from The Matrix Reloaded who held the keys opening hidden doors within the Matrix, allowing Neo to travel swiftly and efficiently. The KeyMaker project aims to play a similar role, providing the keys opening the doors to effective involvement for members of DAOs.

# What is the proposal notifier

The proposal notifier is a tool allowing telegram channel notification when proposal are created on selected DAO, using : 
- boardroom.io API
- n8n worklfow
- telegram bot API
- aifye for summary

# How to deploy

Current workflow version is made to get all boardroom indexed proposals every 10min, filter those indexed during last 10min, filter those corresponding to DAOs we want to get notifications on, generate the summary and send content to corresponding channels (which have to be manually set up).

1. You will need a [n8n](n8n.io) instance, you can either use [n8n.io cloud plan](https://n8n.io/cloud/) or deploy it on your own instance (you can use [this repository](https://github.com/JeanGuillemont/n8n-docker) to deploy it on render.com free offer)
2. Once n8n is setup, create a new worklfow and import [ProposalNotifier file](https://github.com/JeanGuillemont/KeyMarker-ProposalNotifier/blob/main/%20ProposalNotifier.json) by download it from repository and upload on n8n new workflow
3. [Create a boardroom api key](https://boardroom.io/feed/settings/api)
4. Create an airops.com api key, build an app with text input, LLM module with token limit, and following prompt :
What is most important from the following content? Do not repeat yourself or repeat the same sentence structure. Exclude the speaker, adresses. Focus summary on context, funds dedicated, duration of the project, impact on the platform, the application, the protocol, the governance or the token. Be very concise, specific. Write in the tone of the original content. {{text_input}}
5. Follow [Telegram bot documentation](https://core.telegram.org/bots/api#formatting-options) to create your bot
6. Set up all API keys and accounts on n8n workflow
7. Modify frenquencies and DAO filter if required


# Additional links

KeyMaker project - link to come

[Builder profile](https://blockl.ink/@jeanguillemont) (click "Me on Ethereum" to tip if you like/use the project)
