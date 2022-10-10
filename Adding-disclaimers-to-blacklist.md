Disclaimers are added to the blacklist to prevent them from being shown on a given market's website. This guide will take you through the process step-by-step:

1. First, go to the [JIRA page](https://devstack.vwgroup.com/jira/secure/RapidBoard.jspa?rapidView=6730) and assign the ticket to yourself.

_See_ [_here_](https://devstack.vwgroup.com/jira/browse/WECOMMERCE-28696?atlOrigin=eyJpIjoiYjM0MTA4MzUyYTYxNDVkY2IwMzVjOGQ3ZWQ3NzMwM2QiLCJwIjoianN3LWdpdGxhYlNNLWludCJ9) _for an example ticket._

2. Open the [One.Shop - Frontend - OneAudi GitLab repository](https://git.diconium.com/audi/oneshop---oneaudi/oneshop---frontend---oneaudi) in your IDE.
3. Make sure to **pull the latest changes** `git pull` and **create a new branch** `git checkout -b [name of branch]` before making any changes to the code.
4. Check the market that needs the changes (**DE, ES, FR, IT**). The ticket above requests changes to the `DE` market.
5. Navigate to the `disclaimers.ts` file (`src` -> `shared` -> `one shop-configuration` -> `i18n`). Open the market folder that you are making changes to. Again, for this example it would be `DE`.
6. Remove the relevant `DisclaimerKey`. For this example, it is `FinancingAdditionalInformation`:

![Screenshot_2022-04-19_at_15.54.19](uploads/786c90bc91cd3bb88b381dae20219762/Screenshot_2022-04-19_at_15.54.19.png)

_Note: You can find out the `DisclaimerKey` by holding in `command`, hovering over any instance of `DisclaimerKey` in the code and clicking on it. This will open the `index.d.ts` file, which shows all the relevant disclaimer labels and their key:_

![Screenshot_2022-04-19_at_16.00.31](uploads/0eb46f5d6ab97b294a98f54779f3275e/Screenshot_2022-04-19_at_16.00.31.png)


7. Then, navigate to the `__snapshots__` folder and select `create-configurations.test.ts.snap`. Make the same change/s here as you did for the last step

_Note: You can quickly navigate to the relevant part of the code by holding in `control` and `f` simultaneously and then typing `disclaimer`. Again, make sure to change the code for the correct market._

![Screenshot_2022-04-19_at_15.40.47](uploads/401302da1ef841c2a6808751efaecddc/Screenshot_2022-04-19_at_15.40.47.png)


8. Next, you need to add (`git add`) and commit (\`git commit -m "add message here") and then make a merge request on GitLab.
9. Once this is done, you should also make these same changes for the [vwdfive / oneshop-configuration GitHub repository](https://github.com/vwdfive/oneshop-configuration/tree/development/v1/audi).

_If you are not sure how to do step **10** or **11**, then_ [_this page_](https://git.diconium.com/audi/oneshop---oneaudi/oneshop---frontend---oneaudi/-/wikis/Oneshop-configuration:-GitLab-and-GitHub-roadmaps) _will guide you. Start from **vwdfive / oneshop-configuration (GitHub repository)** (after step 1)._

:star2: _Well done! You just made configuration changes to add disclaimers to the blacklist and prevent them from being shown on a given market's website._

> 
>
> [Here](https://git.diconium.com/audi/oneshop---oneaudi/oneshop---frontend---oneaudi/-/merge_requests/1626/diffs#6420d3725b45bed3249150aae3e869b54e4dccfc) is an example of a successful merge request for adding a disclaimer to the blacklist.

_Note: The same process can be done in reverse to remove a disclaimer from the blacklist._