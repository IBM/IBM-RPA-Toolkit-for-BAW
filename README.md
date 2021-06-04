# IBM RPA Toolkit for BAW

## Introduction
As IBM offering management is working on enhancements in out-of-the-box integrations between BAW and IBM RPA, IBM technical sales organization provides this community asset to accelerate and enable usage of IBM RPA together with BAW.

To understand a bit better how the interaction between BAW and IBM RPA actually works, let’s first look at our current bot invocation mechanisms in IBM RPA.

There are several ways to start an IBM RPA bot. Using scheduling, orchestrations (and the underlying queuing infrastructure), Web API and exposing bots as chat bots.

![](./images/start_bot.png)

The Web API is exposed by every IBM RPA agent service that you install and connect to your IBM RPA tenant. The operation of the API is described HERE. Currently the Web API has a fixed port and supports only synchronous (blocking) calls, but it is really easy to use and requires minimal information from your RPA environment:

- URL to your RPA Agent (https://<your_computer_address>:8099)
- Name of the bot you want to trigger
- Version number of the bot you want to trigger (optional)
- Input parameters for the bot (optional)
- Information if the RPA Agent computer needs to be unlocked to run the bot (true / false)

## The Toolkit
The first version of the Toolkit supports running IBM RPA bots synchronously using the Web API. We also plan to support asynchronous calls, but since that part needs some new readiness / custom components on the IBM RPA side, we have not yet implemented that.

When using synchronous calls, there are obviously some things to consider:

- If the bot runs for a long time, we might have a timeout for the call
- If there is no available RPA runtime for bot execution the call fails
- Best suited to run simple bots (queries / updates) with dedicated number of runtimes

Now, finally to the Toolkit itself 😄 Toolkit components are quite well documented already inside the Toolkit using the documentation fields, but let's walk through the components inside the toolkit.

### Toolkit components

![](./images/tk_components.png)

**Business Object**

`RPAInfo` is the BO that you need to use when calling out for your bot. It has the following parameters:
![](./images/rpainfo.png)
- _web_api_url_ (String): the URL pointing to your RPA Agent’s Web API.
- _http_method_ (String): method you want to use, GET or POST are supported, but if you’re passing input parameters, you should always use POST.
- _unlock_machine_ (String): accepts true or false and determines if your agent environment (Windows) needs to be unlocked in order to run the bot.
- _bot_to_trigger_ (String): name of the bot – as it is in your RPA tenant repository – you want to run.
- _bot_version_ (String): version number of the bot you want to run.
- _bot_input_ (String): input parameters that you want to provide when calling the bot – needs to be in JSON String format (look Test Synchronous Integration CSHS for an example).

xxx
