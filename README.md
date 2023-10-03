# OAUTH2

This repository focuses on authorization of users with keycloak auth server. This provides AuthZ with Client Credentials and Authorization Code Grant Type Flow using spring boot application

## Requirements

For development, you will need Sql server, postman and any IDE in your environment.

## Install

#### Step 1: Clone the repository

```bash
git clone https://github.com/AkashP27/OAUTH2.git
```

#### Step 2: Create KeyCloak Server

- Visit [KeyCloak](https://www.keycloak.org/) and install
- To start the server, open terminal in the keycloak directory and use the following command

```bash
bin/kc.bat start-dev --http-port 8180
```

- Open [http://localhost:8180](http://localhost:8180)
- Create keycloak admin account and create a new realm
- Inside the new realm create new client and get its credentials and Valid redirect URIs is `http://localhost/7070/test`
- We need to first add users to KeyCloak to authorize the users in our application
- We can do it manually OR follow this repository [keycloak_add_users](https://github.com/AkashP27/keycloak_user_API.git)

#### Step 3: Provide the credentials

- Open `src/main/resources/application.properties`
- Change the credentials as per your keycloak account and client

#### Step 4: Run MySql scripts
- Create a database and run scripts provided in `src/main/resources/OAuth2.sql`

#### Step 5: Build and run the app using maven

### You can test the API in postman

[Set postman environment from here](https://www.postman.com/akash-api/workspace/akash-public/environment/16112169-8686f9ff-90bd-4624-9292-e6dedb44f4bc?action=share&creator=16112169&active-environment=16112169-8686f9ff-90bd-4624-9292-e6dedb44f4bc)

[![Run in Postman](https://run.pstmn.io/button.svg)](https://app.getpostman.com/run-collection/16112169-4946db6e-5d91-4ea3-9996-9cd219bcd3ec?action=collection%2Ffork&source=rip_markdown&collection-url=entityId%3D16112169-4946db6e-5d91-4ea3-9996-9cd219bcd3ec%26entityType%3Dcollection%26workspaceId%3D9fe04cc0-53c6-4f02-842b-8fe10274477e)

- For Authorization Code Grant Type flow, use `http://localhost:8180/realms/OAuth/protocol/openid-connect/auth?client_id=YOUR_CLIENT_ID&response_type=code&scope=openid&redirect_uri=http://localhost/7070/test&state=asdfghjkl` in your browser which will pop up the consent screen
- Provide user credentials and get the authorization code in the URL itself
