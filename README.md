# Project

Note: this project is for internal use only. We do not monitor or accept outside pull requests

Contains an action that is used to launch a build in Azure DevOps which rebases a PR onto the latest HEAD of its target branch

## Deploying

Release management of the rebase bot action is done though git tags. At present, the current release can be found at `v1.0`.

To deploy your changes, please:

1. Update the tag locally with:
```bash
git tag -f $TAG_NAME
```

2. Push the tag to the remote (https://github.com/xamarin/backport-bot-action):
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

## Trademarks

This project may contain trademarks or logos for projects, products, or services. Authorized use of Microsoft 
trademarks or logos is subject to and must follow 
[Microsoft's Trademark & Brand Guidelines](https://www.microsoft.com/en-us/legal/intellectualproperty/trademarks/usage/general).
Use of Microsoft trademarks or logos in modified versions of this project must not cause confusion or imply Microsoft sponsorship.
Any use of third-party trademarks or logos are subject to those third-party's policies.
