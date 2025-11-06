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

1. Check if you have account in [portal.azure.com](https://portal.azure.com). Use corporate Azure account or see how to [make a new Azure developer subscription](https://dev.to/andrewelans/how-i-enrolled-in-microsoft-365-developer-program-28m6) which can be created with any private email address / phone and credit card
  
  ### My experience
  - I creat subscription with email 250101dev@gmail.com, phone and credit card
  - When accessing portal.azure.com first time with this email, I see only a single user me with email `......#EXT@250101dev.onmicrosoft.com`
  - I adjust the email to `andrew.elans@250101dev.onmicrosoft.com`
  - This email I use further to access:
    - admin.cloud.microsoft - your **main place** to manage Azure account and services:
      - portal.azure.com
      - entra.microsoft.com
      - admin.powerplatform.microsoft.com
      - make.powerapps.com
      - make.powerpages.microsoft.com

  - First time I login to portal.azure.com with `andrew.elans@250101dev.onmicrosoft.com`, the system will ask me to setup MFA authentication with a phone app `Authenticator` that you should have installed prior

  - You get the following licences on your account:
    - Microsoft Power Automate Free -> activated on your user
    - Microsoft Power Apps for Developer -> activated on your user
    - Power Pages vTrial for Makers -> **not** activated on your user

2. Activate **Power Pages vTrial for Makers** licence
    
    This is preffered step over 3. Do it as explained here [learn.microsoft.com/en-us/power-pages/getting-started/trial-signup](https://learn.microsoft.com/en-us/power-pages/getting-started/trial-signup).
    
    After filling out the form you get provisioned a power apps environment in admin.powerplatform.microsoft.com with name `PowerPagesTrial-xxxxxx` and Type `Trial` for 30 days.

    ### Difference between Trial and Developer environments

    Following step 2 you get Trial env which you can convert to `Production` that is a must to make you web site public, see here [learn.microsoft.com/en-us/power-pages/security/site-visibility](https://learn.microsoft.com/en-us/power-pages/security/site-visibility?tabs=new#difference-between-a-private-site-and-a-public-site). Only in public mode you get your public routes to work for MSAL redirect, see **Default pages with public access** here [dev.to/andrewelans/power-pages-spa-login-redirect-2g2n](https://dev.to/andrewelans/power-pages-spa-login-redirect-2g2n).
    
    In step 3 you get a Developer env that you cannot convert to Production and therefore make a Power Pages site public. Trying to convert it in make.powerpowerpages.microsoft.com, the system is sending this req under the hood:

    `POST https://portalsitewide-nor.portal-infra.dynamics.com/api/v1/powerPortal/UpdateSiteVisibility?tenantId=GUID&portalId=GUID&siteVisibility=public`

    with response 400:

    ```json
    {
        "Message": "Site visibility cannot be changed to public on developer environment.",
        "ErrorCode": "D005",
        "ErrorType": "User error"
    }
    ```

    After you have your env provisined, check this page [dev.to/andrewelans/power-pages-spa-main-setup](https://dev.to/andrewelans/power-pages-spa-main-setup-2e0i) for tweaking some things in App registration on portal.azure.com.

3. Step 2 is preffered over this step. Provision a new powerapps environment (take a note on language), power pages portal and set it up as explained here [dev.to/andrewelans/power-pages-spa-main-setup](https://dev.to/andrewelans/power-pages-spa-main-setup-2e0i).

3. Create a new solution in make.powerapps.com [dev.to/andrewelans/power-pages-spa-components-part-1](https://dev.to/andrewelans/power-pages-spa-components-part-1-2oh6)

4. Do some changes to default Power Pages components as per this post [dev.to/andrewelans/power-pages-spa-components-part-2](https://dev.to/andrewelans/power-pages-spa-components-part-2-1d00) and this repo [github.com/AndrewElans/PowerPagesSPA-PowerPagesSetup](https://github.com/AndrewElans/PowerPagesSPA-PowerPagesSetup).
    
    ## Testing portal urls
    
    You should now have a working web site with the following behaviour when requesting urls in a new inkognito window (provide you have enabled Public mode):
      
      - Redirect to login.microsoftonline.com:
        - site-250101.powerappsportals.com
        - site-250101.powerappsportals.com/dynamic-assets
        - site-250101.powerappsportals.com/static-assets
        - site-250101.powerappsportals.com/signin

      - Render Page Not Found:
        - site-250101.powerappsportals.com/page-not-found
        - site-250101.powerappsportals.com/lkjjkdjfkj

      - Render corresponding content:
        - site-250101.powerappsportals.com/cat-pc.png
        - site-250101.powerappsportals.com/access-denied
        - site-250101.powerappsportals.com/_layout/tokenhtml -> blank page with single input on body

    ### Checking dependencies
      
    Log in to your portal with your user. You will see your email on document.body.dataset.emailpowerpages. 
    
    Open Dev Tools -> Sources -> Page. 

    On all these pages the sources will **not** have any of the default power pages dependencies:

      - site-250101.powerappsportals.com
      - site-250101.powerappsportals.com/dynamic-assets
      - site-250101.powerappsportals.com/static-assets
      - site-250101.powerappsportals.com/page-not-found

    Go to `site-250101.powerappsportals.com/access-denied` see all default dependencies loaded and compare to our simplest setup.

    ### Performance

    Dev Tools -> Network

      - site-250101.powerappsportals.com/access-denied (with default deps)
        - 39 requests
        - 1.3 MB transferred
        - 4.8 MB resources (we can deduct the cat image from here to be objective)

      - site-250101.powerappsportals.com (w/o default deps)
        - 1 requests
        - 1.3 kB transferred
        - 382 B resources
    
    Dev Tools -> Performance

      - site-250101.powerappsportals.com/access-denied (with default deps)
        - Scripting 501 ms
        - System 165 ms
        - Loading 18 ms
        - Rendering 14 ms
        - Painting 1 ms
      
      - site-250101.powerappsportals.com (w/o default deps)
        - System 19 ms
        - Rendering 7 ms
        - Scripting 2 ms
    
    And these are very simple pages!

    ## Difference between this setup and default Microsoft Power Pages SPA

    Microsoft now provides SPA functionality as explained here [learn.microsoft.com/en-us/power-pages/configure/create-code-sites](https://learn.microsoft.com/en-us/power-pages/configure/create-code-sites).

    Let's convert our site into the default SPA and see the difference. To do this we add to [settings](https://github.com/AndrewElans/PowerPagesSPA-PowerPagesSetup/blob/main/Site%20Settings/settings.md) `CodeSite/Enabled` set to `true`, resync and compare functionality on the same urls in inkognito.

    - Redirect to login.microsoftonline.com:
        - site-250101.powerappsportals.com *no changes*
        - site-250101.powerappsportals.com/dynamic-assets *no changes*
        - site-250101.powerappsportals.com/static-assets *no changes*
        - site-250101.powerappsportals.com/signin *no changes*

    - Render Page Not Found:
      - site-250101.powerappsportals.com/page-not-found *no changes*
      - site-250101.powerappsportals.com/lkjjkdjfkj **changes**: all default dependences are loaded. This behaviour will have undesired implication on our routing. 

    - Render corresponding content:
      - site-250101.powerappsportals.com/cat-pc.png *no changes*
      - site-250101.powerappsportals.com/access-denied *no changes*
      - site-250101.powerappsportals.com/_layout/tokenhtml *no changes*

5. [Set up MSAL Browser and Vite]() coming...

6. ...

7. ...

8. ...





9. Provision mock json data

11. [Set up Azure Cosmos DB to work with the MSAL token](https://github.com/AndrewElans/PowerPagesSPA-CosmosDB)

Content is in progress...
