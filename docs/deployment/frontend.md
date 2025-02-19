---
title: Deploying the frontend
layout: sub-navigation
order: 7
---

## Notify the team

1. Post a message into di-dev channel in the Data Infrastructure (DDaT) Team saying that you want to do a release and ask if there are any objections. If no objections, proceed with the following steps.

## Tag your release

1. View the current [tags in Data Workspace](https://github.com/uktrade/data-workspace-frontend/tags)

- Make a note of the latest tag
- Check out the master branch and pull the latest.
- Create a new tag from the master branch(see "How to Tag your release")
- Push the new tag to Github

## How to Tag your release

**Format** `v<year>.<month>.<day>`

If there are multiple releases in one day, increment the tag alphabetically starting with `b`. For example `v2024.01.19` then `v2024.01.19.b`, `v2024.01.19.c` and so on.

**Example of how to tag and push**

```shell
git tag -a v2024.01.19 -m v2024.01.19
```

```shell
git push origin v2024.01.19
```

## Create draft release notes

1. View the current [tags in Data Workspace](https://github.com/uktrade/data-workspace-frontend/tags)

- Click on the tag that you just created/pushed
- Use the compare dropdown on the left of the page to compare your tag with the previous released tag to figure out what changes have been made since the last release. This will give you a list of all the changes to be released. Click [latest](https://github.com/uktrade/data-workspace-frontend/releases/latest) to view the latest released tag.
- View the current [releases in Data Workspace](https://github.com/uktrade/data-workspace-frontend/releases)
- Click "Draft a new release"
- Choose the tag you just created
- Click the "[Generate release notes](https://docs.github.com/en/repositories/releasing-projects-on-github/automatically-generated-release-notes)" button
- Check the option "Set as the latest release"
- Click "Save draft"

## Release tag to production

1. Visit the [build job](https://jenkins.ci.uktrade.digital/view/Data/job/data-workspace/) in Jenkins

- Click "build with parameters" and enter the new tag you have created.
- Wait until the `release:staging` job is in a paused state
- Hover over this stage, and click the "Proceed" button
- Wait for the `release: data-workspace` job is complete
- Check the changes in [staging](https://data.trade.staging.uktrade.digital/)
- Click "Proceed" on the `release: prod` job
- Check the changes in [production](https://data.trade.gov.uk/)
- Go back to the [releases in Github](https://github.com/uktrade/data-workspace-frontend/releases)
- Click on the draft release you created earlier
- Click "Publish release"

## Post in the DW channel

Once the release is complete you can then notify everyone in the Data Workspace channel in the Data Infrastructure (DDaT) Team. Use the format below.

```
Data Workspace <tag> has just been released

Whats changed?
<high level description of what has been released>

For more details please see the release notes
```
