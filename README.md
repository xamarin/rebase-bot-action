# Test

Superfluous update as a means to create a test PR for testing rebase triggering within that PR

# Project

Note: this project is for internal use only. We do not monitor or accept outside pull requests

Contains an action that is used to launch a build in Azure DevOps which rebases a PR onto the latest HEAD of its target branch

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft
trademarks or logos is subject to and must follow
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.

## Onboarding

A federated credential needs to be added for each repo where the Rebase bot runs.  Peform the following steps to add the federated credential representing a repo to the [VSEng-AzureDevOps-Xamarin-RebaseBot-Identity](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/resource/subscriptions/7b4817ae-218f-464a-bab1-a9df2d99e1e5/resourceGroups/AzureDevOps/providers/Microsoft.ManagedIdentity/userAssignedIdentities/VSEng-AzureDevOps-Xamarin-RebaseBot-Identity/overview) managed identity
- Navigate to the [federated credentials](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/resource/subscriptions/7b4817ae-218f-464a-bab1-a9df2d99e1e5/resourceGroups/AzureDevOps/providers/Microsoft.ManagedIdentity/userAssignedIdentities/VSEng-AzureDevOps-Xamarin-RebaseBot-Identity/federatedcredentials) section for `VSEng-AzureDevOps-Xamarin-RebaseBot-Identity`
- Click `+ Add Credential`
- Select `Github Actions deploying Azure resources` from the `Federated credential scenario` dropdown
- Fill out the rest of the form as follows. Leave any field not specified below set to its default value.
  - Organization: Name of the GitHub organziation such as `xamarin`
  - Repository: Name of a repo within the organization such as `xamarin-macios`
  - Entity: Select `Branch` from the dropdown
  - Branch: `main` (or the name of the default branch for the repo)
  - Name: Enter a name using the naming format of `[Oranization]--[repo-name]--main-branch` such as `xamarin--xamarin-macios--main-branch`

## Deploying

Release management of the rebase bot action is done though git tags. At present, the current release can be found at `v1.0`.

To deploy your changes, please:

1. Update the tag locally with:
```bash
git tag -f $TAG_NAME
```

2. Push the tag to the remote (https://github.com/xamarin/rebase-bot-action):
```bash
git push --tags --force
```

Please note that for updating the `v1.0` tag (or any other tag you want to push if it already exists), you will need to `push --force` to overwrite the existing tag.

You can list tags by executing the following command

```bash
git tag
```

To view the contents of a tag execute the following command:

```bash
git show $TAG_NAME
```

## Resources

|Resource type|Resource|Resource group|
|:---|:---|:--|
|Rebase Build|[Xamarin Rebase Bot](https://devdiv.visualstudio.com/DevDiv/_build?definitionId=13926)|N/A|
|Telemetry|[Dashboard](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/dashboard/arm/subscriptions/7b4817ae-218f-464a-bab1-a9df2d99e1e5/resourcegroups/dashboards/providers/microsoft.portal/dashboards/6d818688-e99e-4055-8e54-b1f4d94be218)|[PipelineTelemetry](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/resource/subscriptions/26b9b438-7fe8-482f-b732-ea99c70f2abb/resourceGroups/pipelinetelemetry/overview)|
|Managed identity|[VSEng-AzureDevOps-Xamarin-RebaseBot-Identity](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/resource/subscriptions/7b4817ae-218f-464a-bab1-a9df2d99e1e5/resourceGroups/AzureDevOps/providers/Microsoft.ManagedIdentity/userAssignedIdentities/VSEng-AzureDevOps-Xamarin-RebaseBot-Identity/overview)|[AzureDevOps](https://ms.portal.azure.com/#@microsoft.onmicrosoft.com/resource/subscriptions/7b4817ae-218f-464a-bab1-a9df2d99e1e5/resourceGroups/AzureDevOps/overview)|
