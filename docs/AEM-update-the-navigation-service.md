WIP

## Steps to check the navigation configuration from the browser

- go to test-www or pre-www of the relevant market
- right click and go to inspect
- click on console tab
- in the console, copy and paste the following line and press enter:
`window.SETUPS.get('navigationServiceOptions')` ;

![pdp-it](uploads/d6aabce50665ea2e6ed33edabfc6072c/pdp-it.png)

In the above screenshot, you can see the result. One of the paths is highlighted as an example.

## Steps for AEM changes

- after this, login to AEM (test or pre)
- go the settings page (click on gear icon)
![Screenshot_2022-05-16_at_10.46.59](uploads/e0693d9170866630bbbd0afd3cf82ee5/Screenshot_2022-05-16_at_10.46.59.png)
- then click on nemo from the folder structure
![Screenshot_2022-05-16_at_10.49.17](uploads/fd915a41ff85c085292b1c866e68eae8/Screenshot_2022-05-16_at_10.49.17.png)
- then go to market folder (for example IT)
- then select the json folder from the market
![Screenshot_2022-05-16_at_10.50.59](uploads/5a2dded2415787042845d1c9109f4425/Screenshot_2022-05-16_at_10.50.59.png)
- then double click on oneshop-navig-service.json from the left sidebar (this will open an empty page)
- download the file by removing `miscadmin#/` from the url (see screenshot below):

![download-aem](uploads/797b9267620271aa13db64ced6a21b60/download-aem.png)

- open this file in your IDE and edit as per requirement
- upload the changed file to the json folder and then activate it. Make sure you delete or replace the old file

## Common issues

If you find that the changes did not work then it may be a caching issue.

Taking the first screenshot as an example, you can see the path highlighted for the PDP. This is actually the old path which has been cached:

![pdp-it](uploads/d6aabce50665ea2e6ed33edabfc6072c/pdp-it.png)

In the following screenshot, we have cache busted the page (add ? and any random letters after `html` in the url). You can see in the screenshot how to do this. When we do this cache busting, you can see that the new and correct path is now loaded:

![pdp-it-cache-bust](uploads/cdf18835f82b8ed0b3d27e31cb9309ed/pdp-it-cache-bust.png)

In order to resolve this issue, we have to leave a comment to Tobias Menzel on the relevant ticket telling him that the issue is a caching issue and that the cache needs to be flushed.
