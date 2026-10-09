JENKINS

## Jenkins: a practical mental model

Jenkins automates a sequence of software-delivery steps. The **controller** coordinates jobs and stores configuration; **agents** run the work; a **Pipeline** describes stages such as checkout, build, test, package, and deploy. A `Jenkinsfile` keeps that pipeline definition beside the application code so changes can be reviewed with the code.

### Build a safe first pipeline

1. Create a small sandbox Jenkins controller and one build agent, then keep the controller's administrative interface private.
2. Add a Pipeline job and point it to a repository containing a `Jenkinsfile`.
3. Start with checkout, a deterministic build, and automated tests. Publish a versioned artifact only after checks pass.
4. Store repository/deployment credentials in Jenkins Credentials and expose them only to the stage that needs them. Never print secrets into console logs or commit them to the `Jenkinsfile`.
5. Add a manual approval before a production deployment; configure timeouts, test reports, logs, and a rollback strategy.

### Remember the moving parts

**controller schedules → agent executes → stage reports → artifact moves forward**. Plugins add features but also expand the security and maintenance surface, so keep them current and install only what the job needs. A successful pipeline means its configured checks passed; review the test coverage and deployment health separately.

**Recall check:** A job is stuck waiting and no logs appear. Check whether an eligible agent is online and has the required label/executor.

