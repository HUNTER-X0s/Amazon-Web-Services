# Amazon API Gateway: Console Walkthrough

**Mental model:** API Gateway is the managed front door for an API. A route/method selects an integration; an optional authorizer controls who may call it; a stage provides a deployed URL and lifecycle boundary.

Related note: [API.md](../../API.md)

## Build a small HTTP API with Lambda

1. Create a harmless test Lambda function first, and confirm its execution role and response shape.
2. Open [API Gateway](https://console.aws.amazon.com/apigateway/) and choose **Create API → HTTP API → Build**.
3. Choose **Add integration → Lambda**, select the intended function and Region, and enter a neutral API name.
4. Create a route such as `GET /hello` and link it to the Lambda integration. Review the generated invoke permission on the function.
5. Review stage/deployment settings. For learning, use a clearly named test stage. For production, configure authentication/authorization (for example JWT, IAM, or Lambda authorizer as appropriate), throttling, CORS, logging, and custom-domain TLS deliberately.
6. Choose **Create** or **Deploy** as shown for the API type. Copy the invoke URL from the stage details.
7. Call the route with a non-sensitive test request and confirm the response, API access logs, and Lambda logs.

## REST API alternative

Choose a REST API when its feature set is needed. Create the API, resources, methods, and integration; configure method authorization; deploy to a stage; then test the stage invoke URL. Creating methods alone does not publish them—the API must be deployed.

## Verify and clean up

Confirm the route, integration, authorizer, stage, invoke URL, throttles, and log settings. Delete the API and dedicated test Lambda only when no client depends on them. Custom domains, certificates, CloudWatch logs, and data transfer may be separate resources/costs.

**Remember:** **route matches → authorizer decides → integration runs → stage exposes**.

**Official references:** [Get started with a REST API](https://docs.aws.amazon.com/apigateway/latest/developerguide/getting-started-rest-new-console.html) · [Create an HTTP API](https://docs.aws.amazon.com/apigateway/latest/developerguide/http-api-develop.html)
