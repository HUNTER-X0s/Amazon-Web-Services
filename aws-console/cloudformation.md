# AWS CloudFormation: Console Walkthrough

**Mental model:** A template describes the desired resources; a stack is CloudFormation managing those resources together. Review the proposed change set as carefully as you would review a production deployment.

Related note: [AWS CloudFormation IAC.md](../../AWS%20CloudFormation%20IAC.md)

## Launch a template safely

1. Prepare a reviewed YAML/JSON template. Inspect every resource, IAM policy, public endpoint, encryption setting, retention policy, and any `DeletionPolicy`/replacement behavior.
2. Open [CloudFormation](https://console.aws.amazon.com/cloudformation/), confirm the Region, and choose **Stacks → Create stack → With new resources (standard)**.
3. Upload a local template or provide an authorized S3 template URL. Run template validation and resolve errors before continuing.
4. Enter a unique stack name and parameter values. Never put passwords or API secrets directly in the template; reference Secrets Manager or a secure parameter mechanism.
5. Review stack options, tags, rollback behavior, and execution role. If the template creates IAM resources, acknowledge the required capabilities only after inspecting those resources.
6. On the review page, create a change set when available. Inspect resources that will be added, modified, replaced, or removed.
7. Submit/create the stack only after review. Open **Events** and wait for `CREATE_COMPLETE`; if it fails, read the first failed event and its reason.
8. Read the **Outputs** tab for endpoints and IDs. Verify the created resources in their own service consoles.

## Update or remove a stack

For updates, submit the changed template and inspect/execute a change set. For cleanup, confirm the stack owns the resources and that data has been backed up. Choose **Delete** only when removal is intended; retained resources (such as buckets or snapshots) can remain billable. Avoid manual edits to stack-owned resources because they can create drift.

**Remember:** **template → parameters → change set → stack events → outputs**.

**Official references:** [Create a stack in the console](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/cfn-console-create-stack.html) · [First stack walkthrough](https://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/gettingstarted.walkthrough.html)
