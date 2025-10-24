# PowerPages-SPA

Sample project of a Microsoft Power Pages Single Page Application with **no** "low code no code" principle. Includes Vite as devDependency and optional Node.js hosted as Azure Web App. Suitable for corporate environment with sensitive business data.

## Features
  - Fully controlled dependencies in Power Pages
  - Browser-based [Microsoft Authentication Library for JavaScript](https://github.com/AzureAD/microsoft-authentication-library-for-js/tree/dev/lib/msal-browser) authenticating with
    - Azure AD
    - Dataverse (db behind Power Pages)
    - Azure Storage
  - Role-based access control to resources and content
  - Lightweight
  - Custom logger
  - Multi-layered security on various levels
  - Techstack is limited only to Azure cloud-based tools (SaaS)
  - Pulling data from API endpoints with Flows or custom Node.js Web App
  - Syncing data with Dataflows
  - Optional Domain-Driven Design with Node.js Web App
    - Simple setup
    - Node.js as a proxy-server
    - Isolate business logic from system code

## Sample project

Supplier management portal to provide a buyer/procurement proffesional with information on suppliers organization is dealing with. The portal will keep internal stakeholders updated with current supplier status including challenges, delays and quality issues supplier is experiencing in projects or other engagements, prices and lead times actual vs committed, legal issues, evaluation of suppliers and more. The aim of the portal is to make buyer's work easier and more efficient, improve bargaining power in negotiations with suppliers and help take right business decisions during supplier selection to maintain "5 rights of procurement".

## Steps

1) Check access to [portal.azure.com](https://portal.azure.com). Use corporate Azure account or [make a new Azure developer subscription](https://dev.to/andrewelans/how-i-enrolled-in-microsoft-365-developer-program-28m6). 
2) Create a new Power Pages page.

Content is in progress...
