# Documentation for ${{values.app_name}}

This application is a template for test and create components using Backstage and standard for pipeline creation using GitHub Actions, Helm, Kubernetes and ArgoCD.
Is possible explore all the flow using CI/CD and configurations needs for this.
Exist a endpoint for test the application:
- `/api/v1/details`

You can access using URL **http://${{values.app_name}}-${{values.app_env}}.localtest.me/api/v1/details**

```json
{
	hostname: "${{values.app_name}}-${{values.app_env}}-xpto",
	message: "New attribute message for test cicd!!",
	time: "2025-09-17T13:58:31.212528637Z"
}
```
