# AWS Amplify Hosting: Console Walkthrough

**Mental model:** Amplify connects a source branch to a managed build-and-hosting pipeline. A successful build creates a deployment; future commits to the connected branch can deploy automatically.

Related note: [AWS Amplify.md](../../AWS%20Amplify.md)

## Deploy from a Git repository

1. Confirm the repository contains a working frontend app, build scripts, and no committed secrets. Know the build command and output directory.
2. Open [AWS Amplify](https://console.aws.amazon.com/amplify/), choose **New app → Host web app**, then select your Git provider and continue.
3. When the GitHub authorization screen appears, grant Amplify access only to the specific repository needed for this app if possible. This step changes third-party repository permissions; review the requested scope before approving.
4. Choose the repository and branch. Review the detected framework and build settings; correct the build command and artifact output directory if needed.
5. Configure environment variables without placing secrets in source control. Use a secure secrets mechanism for sensitive values and restrict access to build logs/settings.
6. Review app name, branch, service role, build settings, and domain visibility. Choose **Save and deploy**.
7. Watch the build phases. When deployment is **Deployed**, open the generated URL and test the app. Add preview branches or a custom domain only after the first deployment works.

## Verify and clean up

Confirm the deployed commit, build logs, branch mapping, domain, and access settings. Disconnect repository permissions when the app is no longer needed. Deleting an Amplify app may not delete every related backend resource, domain, or custom build artifact; inspect them separately. Build minutes, storage, and data transfer can be charged.

**Remember:** **source branch → build settings → artifact → CDN URL**.

**Official references:** [Welcome to Amplify Hosting](https://docs.aws.amazon.com/amplify/latest/userguide/welcome.html) · [Connect GitHub](https://docs.aws.amazon.com/amplify/latest/userguide/setting-up-GitHub-access.html)
