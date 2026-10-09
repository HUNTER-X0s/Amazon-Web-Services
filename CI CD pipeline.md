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

