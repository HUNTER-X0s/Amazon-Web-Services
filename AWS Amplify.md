AWS Amplify 



Amplify is a platform that simplifies

* Building
* Deploying and
* Hosting full-stack web and mobile apps.



* It connects to backend services like user logging, data storage, and APIs. 
* Offers hosting an automatic update for web apps 



* Speeds up app development with built-in tools 
* Provide scalable backend services that can grow with your app. 
* Simplifies cloud integration, making it easier for beginners and experienced developers 

## Remember Amplify as a managed app pipeline

For Amplify Hosting, follow this chain: **repository branch → build settings → generated artifacts → hosted deployment → CDN URL**. A successful deployment is tied to a commit, which makes it possible to compare build logs and roll back to a known version. Frontend hosting and backend resources are related parts of an app, but have separate configuration and permissions.

Before connecting a source provider, inspect which repositories Amplify can access. Keep credentials out of source and build output; store sensitive configuration in an approved secrets service. Review redirects, custom domains, and branch visibility before sharing the generated URL.

**Recall check:** A branch deploys but displays a blank page. Which two build details should you check first? The build command and artifact/output directory.

**Console practice:** [Amplify Hosting walkthrough](guides/aws-console/amplify-hosting.md)



































































