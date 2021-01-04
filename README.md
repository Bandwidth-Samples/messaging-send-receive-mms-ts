# Send and Receive MMS
<a href="http://dev.bandwidth.com"><img src="https://s3.amazonaws.com/bwdemos/BW-VMP.png"/></a>
</div>

 # Table of Contents

<!-- TOC -->

- [Send and Receive MMS](#send-and-receive-mms)
- [Description](#description)
- [Bandwidth](#bandwidth)
- [Environmental Variables](#environmental-variables)
- [Callback URLs](#callback-urls)
    - [Ngrok](#ngrok)

<!-- /TOC -->

# Description
Using a tool capabable of posting (Postman) post a json body to the apps endpoint `/messages` with a json body like:
```json
{
  "to": "+19994444",
  "text":"Hello World!"
}
```
The application will text the number `+19994444` a picture of a cat and the words `Hello World!`.
If you text you Bandwidth number any media file after setting up the application's callback in the bandwidth dashboard; it will save it to the project folder.

# Bandwidth

In order to use the Bandwidth API users need to set up the appropriate application at the [Bandwidth Dashboard](https://dashboard.bandwidth.com/) and create API tokens.

To create an application log into the [Bandwidth Dashboard](https://dashboard.bandwidth.com/) and navigate to the `Applications` tab.  Fill out the **New Application** form selecting the service (Messaging or Voice) that the application will be used for.  All Bandwidth services require publicly accessible Callback URLs, for more information on how to set one up see [Callback URLs](#callback-urls).

For more information about API credentials see [here](https://dev.bandwidth.com/guides/accountCredentials.html#top)

# Environmental Variables
The sample app uses the below environmental variables.
```java
BANDWIDTH_ACCOUNT_ID                 // Your Bandwidth Account Id
BANDWIDTH_USERNAME                   // Your Bandwidth API Token
BANDWIDTH_PASSWORD                   // Your Bandwidth API Secret
BANDWIDTH_PHONE_NUMBER                // Your The Bandwidth Phone Number (E164 Format)
BANDWIDTH_MESSAGING_APPLICATION_ID   // Your Messaging Application Id created in the dashboard
PORT                                 // The port number you wish to run the sample on
```

# Callback URLs

For a detailed introduction to Bandwidth Callbacks see https://dev.bandwidth.com/guides/callbacks/callbacks.html

Below are the callback paths:
* `/callbacks/messageCallback`

## Ngrok

A simple way to set up a local callback URL for testing is to use the free tool [ngrok](https://ngrok.com/).  
After you have downloaded and installed `ngrok` run the following command to open a public tunnel to your port (`$PORT`)
```cmd
ngrok http $PORT
```
You can view your public URL at `http://127.0.0.1:{PORT}` after ngrok is running.  You can also view the status of the tunnel and requests/responses here.
