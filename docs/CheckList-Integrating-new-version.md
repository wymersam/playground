This is the process to follow after a new WhiteLabel version is released.

## Ticket process

1. Go to the [JIRA page](https://devstack.vwgroup.com/jira/secure/RapidBoard.jspa?rapidView=6730) and assign the ticket to yourself

_See [here](https://devstack.vwgroup.com/jira/browse/WECOMMERCE-32247) for an example ticket._

![Screenshot_2022-04-14_at_09.20.30](uploads/e3f3d6957959620e4a71a93ee3cd2e73/Screenshot_2022-04-14_at_09.20.30.png)

2. Check for any **breaking changes** in the release notes

_See [here](https://github.com/vwdfive/oneshop-wlfe/releases/tag/PI22.1.2.0) for an example._

![Screenshot_2022-04-14_at_09.24.00](uploads/8fc4bc38a7d31f993c2dc8fc0c14669d/Screenshot_2022-04-14_at_09.24.00.png)

## Code integration

1. Open the One.Shop - Frontend - OneAudi repository in your IDE
2. Run the following command in the terminal to see the latest version: `npm info @vwdfive/oneshop-wlfe` or manually update the version if you already know it

_In the example below, you can see that the new version for `PI22.1.2.1` is `11.3.0`._

![Screenshot_2022-04-14_at_09.51.31](uploads/e09f4244ba852cf6e6fa034ecf3fc904/Screenshot_2022-04-14_at_09.51.31.png)

3. Update the patch files - check the workaround list and see if it has been fixed in the new version. The patch file can be found in `patches`. You will also need to update the name of the file to the new version. For the example below, you would need to change `@vwdfive+oneshop-wlfe+11.1.1.patch` to `@vwdfive+oneshop-wlfe+11.3.0.patch`

![Screenshot_2022-04-21_at_09.21.33](uploads/5bec04303c6f9aa6503d9535d1a2ea83/Screenshot_2022-04-21_at_09.21.33.png)

4. Update the docker image as per the release. To do this, navigate to `.gitlab-ci.yml`. Press `command` and `f` and then search for `BFF_DOCKER_IMAGE`. Change the version at the end of this line to the new version.

![Greenshot_2022-07-08_11.18.05](uploads/12caf3b29e91b6a360a955c0b94c3b6b/Greenshot_2022-07-08_11.18.05.png)

5. Update all the dependencies and dev dependencies. To do this, navigate to `package.json` and find all instances of the old version. You can do this by pressing `command` and `f` and then searching for the old version e.g. `11.1.1`. You can select all instances of this old version by pressing `command` and `d`. You should update all of these instances to the new version e.g. `11.3.0`

![Screenshot_2022-04-21_at_09.15.12](uploads/e76c968153154db262b52b96632cd8fb/Screenshot_2022-04-21_at_09.15.12.png)

## Build Process

1. Run `npm run setup`. Do this **twice**
2. Check if any changes need to be done in the code by running: `npm run cqa`. The change you need to make will be shown as errors in the terminal.
3. Run the local E2E testing: `npm run cypress:open`
4. Make sure `Storybook` is running and then run: `npm run start`
5. Check if any snapshots need to be updated: `npm run test`

## .. continue on process

1. Create the merge request (MR). Simply go to the [GitLab repository](https://git.diconium.com/audi/oneshop---oneaudi/oneshop---frontend---oneaudi) and create this merge request
2. Assign to reviewers (these should be the other devs on your team)
3. Check the pipeline. When all the ticks are green, this means the tests have passed

![Screenshot_2022-04-14_at_09.35.12](uploads/cdadac2038c47e1ae9b8b855ea5636e8/Screenshot_2022-04-14_at_09.35.12.png)

4. If all the tests pass, go to the [JIRA page](https://devstack.vwgroup.com/jira/secure/RapidBoard.jspa?rapidView=6730) and assign the ticket to a reviewer with the MR details
5. Once the code review is done, **deploy the BFF and Feature App MarketPlace**
for deployment refer [how to deploy on marketplace](https://git.diconium.com/audi/oneshop---oneaudi/oneshop---frontend---oneaudi/-/wikis/how-to-deploy-on-marketplace)

![Screenshot_2022-04-27_at_11.58.15](uploads/6645d72d033544f1db8a41be94f6f31d/Screenshot_2022-04-27_at_11.58.15.png)
![Screenshot_2022-04-27_at_11.58.22](uploads/10a3c2ac946093629d7586bbaa5b6253/Screenshot_2022-04-27_at_11.58.22.png)

6. After the deployment is done, do the happy path testing once
7. Then go to the [JIRA page](https://devstack.vwgroup.com/jira/secure/RapidBoard.jspa?rapidView=6730) and assign the ticket to the testing team with the deployed details
8. Finally, write an update in the team channel regarding deployment
