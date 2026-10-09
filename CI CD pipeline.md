CI/CD 





Continuous Integration and Continuous Delivery, a foundational concept in DevOps. 

It explains why these practices are essential for modern software development and how they optimize the development life cycle.





* Core Concepts of CI/CD
* Software Development Life Cycle (SDLC): The video outlines the flow of application changes, including feature development, committing/pushing to branches, building, testing, and deployment 
* Continuous Integration (CI): Automating the build and test stages of code changes to ensure that new code integrates seamlessly with the existing codebase 





Continuous Delivery vs. Continuous Deployment (CD):

* Continuous Delivery: Involves automated deployment to staging, followed by a manual approval step before reaching production 
* Continuous Deployment: Automates the entire process, including the transition to production, without requiring manual intervention 





Why We Need CI/CD

* Manual processes in software development are often time-consuming and error-prone. The video highlights several problems that arise without automation, such as:
* Integration Hell: Difficulty merging code from multiple developers 
* Manual Testing Bottlenecks: Leading to slower release cycles and increased bugs 
* Inconsistent Releases: Difficulty rolling back to previous versions, which historically discouraged weekend or Friday deployments 





Implementation and Tools

* Automation Scripts: CI/CD pipelines are often implemented using YAML configuration files 
* Popular Tools:  Circle, Travis, GitLab, Mercurial. GitHub Actions and Jenkins (a powerful but slightly harder-to-maintain orchestrator) 





Deployment Strategies

* To achieve near-zero downtime, the video explains several deployment strategies used alongside CI/CD:
* Blue-Green Deployment: Using two identical environments (Blue for current, Green for new) to allow for instant switching and easy rollbacks 
* Canary Deployment: Gradually shifting traffic to the new version for a small percentage of users to verify stability before a full rollout 
* Rolling Deployment: Replacing instances one by one behind a load balancer to minimize service disruption 

## Remember CI/CD as a feedback loop

CI asks: **does this change integrate and pass checks?** Delivery asks: **is a tested change ready for a controlled release?** Deployment asks: **has the change reached production automatically?** A pipeline commonly moves through source control, build, automated tests, artifact storage, deployment, and health checks; each stage should make a clear decision before the next one proceeds.

Keep build artifacts immutable, store credentials in the pipeline's secret facility, and make deployment steps repeatable. A green build is evidence that configured checks passed—not proof that every user scenario works. Use canary, blue/green, or rolling releases to limit impact and define rollback signals in advance.

**Recall check:** Tests pass but production health drops after release. What should happen? Halt or roll back based on the release policy, inspect logs/metrics, then fix and redeploy through the pipeline.

