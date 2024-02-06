---
title: "OAuth 2 Simplified "
date: 2024-02-06T06:55:46+05:30
---

## OAuth 2 Simplified 

OAuth stands for **Open Authorization**. It provides a Standardized Protocol for authorization to enable secure access to protected data stored in 3rd party resources. You may encounter logins via "Gmail" / "Facebook" / "GitHub". Check the log-in screen of an application below

![alt text](/img/login-screen-oauth.png)

Let's delve into the depths of the initial level.

### Actors involved 

Let's assume that Radha wants to login into her newspaper application(for eg- https://www.thehindu.com/) via Gmail.com.

**4 Actors** involved in the OAuth framework 

1. Resource Owner
2. Client application
3. Authorization Server
4. Resource Server

The diagram below illustrates four actors based on the example provided above.

![alt text](/img/oauth-4-actors.png)



### Authorization Grant Types

Authorization Grant Type is provided by the client to get an access token from the Authorisation Server. There are 5 mechanisms used by the client to Obtain Access Tokens from the Authorization Server.


1. Authorization Code Grant
3. Refresh Token Grant
2. Client Credential Grant
3. Implicit Grant
4. Resource Owner Password Credential Grant


In this blog post, I am covering the Authorization Code Grant flow

### OAuth 2 Flow

Let me try to explain the flow using the above example given by the Actors involved.

As first first newspaper application will register into Gmail and Gmail provide ClientId and Secret. Please keep in mind that this is a one-time activity between the newspaper application and the Gmail Server. So the Gmail Server can identify the newspaper application.

Assume that **user: Radha** wants to log into the **newspaper application** via **Gmail.com.**


![alt text](/img/oauth-flow-auth-code-grant.png)

Let's go through the diagram

**Steps 1 to 3:** When Radha hits Login via Gmail.com, it will redirect to Gmail.com., where Radha can log into Gmail using her credentials and provide consent to access her data. 

**Step 4:** After providing consent redirect back to the Newspaper application with authentication code. 

**Step 5 to 6:** Next, the Newspaper Application requests for Access Token using the authentication code and Gmail.com provides an Access Token and Refresh Token.

**Steps 7 to 10:** After receiving an access token, the newspaper application requests Gmail.com to access secure Data(eg - email, DoB, contact details etc) using the access token. Gmail will provide data if a valid token

**Step 11:** Radha will see a successful Login message in the Newspaper application.


Next, I will cover other Authorization Grant Types


Here are a few sources for some extra on this topic:

- [OAuth 2.0: Explained with API Request and Response Sample](https://youtu.be/3Gx3e3eLKrg?si=GkPjPgpc5H6SzpQj)
- [Modern Guide - What is OAuth 2.0 and How Does It Work?](https://fusionauth.io/articles/oauth/modern-guide-to-oauth)