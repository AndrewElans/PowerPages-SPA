# Power Pages SPA

Sample project of a Microsoft Power Pages Single Page Application with **no** "low code no code" principle. Provisioned with Vite and optional Node.js hosted as Azure Web App. Suitable for corporate environment with sensitive business data.

## Features
  - Fully controlled dependencies in Power Pages
  - Sign-in with multiple accounts / switch accounts made easy without signout
  - Browser-based [Microsoft Authentication Library for JavaScript](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser) authenticating with:
    - Azure AD
    - Dataverse (db behind Power Pages)
    - Azure Storage
    - Azure Cosmos DB
  - Role-based access control to resources and content
  - Lightweight
  - Custom logger
  - Multi-layered security on various levels
  - Techstack is limited to Azure SaaS cloud-based tools only
  - Pulling data from API endpoints with Flows or custom Node.js Web App
  - Syncing data with Dataflows
  - Optional Domain-Driven Design with Node.js Web App
    - Simple setup
    - Node.js as a proxy-server
    - Isolate business logic from system code

## References
  - [Default dependencies in Power Pages](https://dev.to/andrewelans/login-redirect-in-power-pages-spa-with-hash-and-query-params-4o5)
  - ...
## Sample project description

Supplier management portal to provide a buyer/procurement proffesional with information on suppliers organization is dealing with. The portal will keep internal stakeholders updated with current supplier status including challenges, delays and quality issues supplier is experiencing in projects or other engagements, prices and lead times actual vs committed, legal issues, evaluation of suppliers and more. The aim of the portal is to make buyer's work easier and more efficient, improve bargaining power in negotiations with suppliers and help take right business decisions during supplier selection to maintain "5 rights of procurement".

## Steps
1) Check if you have account in [portal.azure.com](https://portal.azure.com). Use corporate Azure account or see how to [make a new Azure developer subscription](https://dev.to/andrewelans/how-i-enrolled-in-microsoft-365-developer-program-28m6) which can be created with any private email address / phone and credit card
   - I created the subscription with email 250101dev@gmail.com
   - When accessing portal.azure.com first time with this email, I see only a single user me with email `...blabla...EXT#@250101dev.onmicrosoft.com`
   - I adjust the email to `andrew.elans@250101dev.onmicrosoft.com`
   - This email I will use further to access:
     - portal.azure.com
     - make.powerapps.com
     - make.powerpages.microsoft.com
     - admin.powerplatform.microsoft.com
   - First time I will login to portal.azure.com with `andrew.elans@250101dev.onmicrosoft.com`, the system will ask me to setup MFA authentication with a phone app `Authenticator` that you should have installed prior
2) Provision a new powerapps environment (take a note on language), power pages portal and set it up as explained here [dev.to/andrewelans/power-pages-spa-main-setup](https://dev.to/andrewelans/power-pages-spa-main-setup-2e0i)
3) Create a new solution in make.powerapps.com [dev.to/andrewelans/power-pages-spa-components-part-1](https://dev.to/andrewelans/power-pages-spa-components-part-1-2oh6)
6) Do some changes to default Power Pages components as per this post []()
7) 
8) ...
9) ...
10) ...
11) Provision mock json data
12) [Set up MSAL Browser](https://github.com/AndrewElans/PowerPagesSPA-MSAL-Browser) repo in progress
13) [Set up Azure Cosmos DB to work with the MSAL token](https://github.com/AndrewElans/PowerPagesSPA-CosmosDB)

Content is in progress...
