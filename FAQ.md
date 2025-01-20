# Frequently Asked Questions
* [I got a connection error after I click on the Azure login link and login to my Microsoft account.](#i-got-a-connection-error-after-i-click-on-the-azure-login-link-and-login-to-my-microsoft-account)
* [I got `KeyError: 'access_token'` after I copied the link](#i-got-keyerror-accesstoken-after-i-copied-the-link)
* [I got `Subprocess Mineflayer failed to start` error.](#i-got-subprocess-mineflayer-failed-to-start-error)
* [I saw the bot left and rejoin the game after each task.](#i-saw-the-bot-left-and-rejoin-the-game-after-each-task)
* [How to show the bot's first-person perspective?](#how-to-show-the-bots-first-person-view)
* [Can I use GPT-3.5 instead of GPT-4?](#can-i-use-gpt-35-instead-of-gpt-4)
* [What's the estimated cost of running the agent?](#whats-the-estimated-cost-of-running-the-agent)

## I got a connection error after I click on the Azure login link and login to my Microsoft account.

It's normal that you get a connection refused or 404 error after you log in. You will still see the new URL in your browser. You just need to copy and paste that link. It should contain things like `code=M.C....` in that link.

## I got `KeyError: 'access_token'` after I copied the link

While testing, we use Redirect URI Type: `Public client/native (mobile & desktop)` in the app registration for Azure Login. You can try both "Web" and "Public client" URI Types to determine which one works for you. If all approaches fail, please refer to the original tutorial in [minecraft-launcher-lib](https://minecraft-launcher-lib.readthedocs.io/en/stable/tutorial/microsoft_login.html).

## I got `Subprocess Mineflayer failed to start` error.

There are many reasons that may cause this problem. You can try with following solutions:
1. Make sure you install nodejs and the dependency packages correctly. You can use the following command to check your installation:
    ```bash
    cd voyager/env/mineflayer
    node index.js
    ```
   If you see `Server started on port {PORT}`, then your installation is correct. You can kill the process by `Ctrl+C`.
2. Make sure you install Fabric correctly. You should be able to select the Fabric version in the Minecraft launcher. 
3. Each Mineflayer process can only listen to one port. If you want to start multiple instances, you need to manually change the port when initialization:
    ```python
    from ai_minecraft import Agent
    agent = Agent(
        server_port=3001, # default is 3000
        ...
    )
    ```

## I saw the bot left and rejoin the game after each task.

After completing each task, we'll reset the environment, which means the bot will exit and rejoin the game. This reset is necessary to synchronize Mineflayer with the Minecraft game. We do this because certain commands we utilize might result in lag on the Mineflayer side, causing the inventory stored in Mineflayer to differ from the actual inventory in the game. However, if you wish to avoid the reset, you can use `agent.learn(reset_env=False)` and consider increasing the `env_wait_ticks` value. This will provide Mineflayer with additional time to sync with the Minecraft game.

## How to show the bot's first-person view?

Due to Mineflayer's limitation, we currently cannot directly get the bot's view in the game. Although there's a plugin called [prismarine-viewer](https://github.com/PrismarineJS/prismarine-viewer), the video quality is not good enough, so we opt not to use it.

## Can I use GPT-3.5 instead of GPT-4?

It's highly recommended to use GPT-4. GPT-3.5 falls behind in terms of code quality and reasoning ability compared to GPT-4. Moreover, GPT-3.5 has a limited context length, which means it may provide incomplete responses. If you insist on using GPT-3.5, it is essential to configure it with `skill_manager_retrieval_top_k` ≤ 2 to reduce the context length of the prompt.

## What's the estimated cost of running the agent?

Using the agent for approximately 160 iterations using GPT-4 will cost you around 50 USD. It's important to keep a close eye on your OpenAI API expenses and avoid unnecessary spending. Once the agent begins running, it's recommended to monitor the bot's behavior for a period and ensure that it successfully completes some tasks.