# IBM RPA Toolkit for BAW

## Introduction
As IBM offering management is working on enhancements in out-of-the-box integrations between BAW and IBM RPA, IBM technical sales organization provides this community asset to accelerate and enable usage of IBM RPA together with BAW.

To understand a bit better how the interaction between BAW and IBM RPA actually works, let’s first look at our current bot invocation mechanisms in IBM RPA.

There are several ways to start an IBM RPA bot. Using scheduling, orchestrations (and the underlying queuing infrastructure), Web API and exposing bots as chat bots.

![](./images/start_bot.png)

The Web API is exposed by every IBM RPA agent service that you install and connect to your IBM RPA tenant. The operation of the API is described HERE. Currently the Web API has a fixed port and supports only synchronous (blocking) calls, but it is really easy to use and requires minimal information from your RPA environment:

•	URL to your RPA Agent (https://<your_computer_address>:8099)
•	Name of the bot you want to trigger
•	Version number of the bot you want to trigger (optional)
•	Input parameters for the bot (optional)
•	Information if the RPA Agent computer needs to be unlocked to run the bot (true / false)
