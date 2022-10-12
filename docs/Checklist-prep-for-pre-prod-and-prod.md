This page only for checklist to check while pre-prod process

For more details regarding the steps refer [Release-Process](https://git.diconium.com/audi/oneshop---oneaudi/oneshop---frontend---oneaudi/-/wikis/Release-Process)

- Release ticket is normally created by Service and Operations (S&O) Team ticket: WEONESUPP-XYZ.
- Communication Channel uses in this process

  - RocketChat(Audi)
  - Team(internal)

Pre-prod:

## PR for AEM changes

Create a PR on audi-feature=app-regsitry-aem: change existing entiy in registry file so that we can point version on the AEM

## AWS

- if newly added AWS client and secret on the pre-prod based on the market , documentation commands, it will be helpful while production development

## Log's

- Check logs in stratos , if you notice any error please add the details so that we don't need to panic  or start the investigation on that error.
- if we can resolve the error the prep-prod please add action point with the solutions

## AEM

- Update the document which version is going to live , pre-www, test-www

## WLFE-BFF

- Update the document which version of docker image is deployment  with date

## TROM

- Close all the PR for configuration , align with team for Integration ,Integration_rc branch

## Contact Person  

- AEM (Tobias Menzel)
- Service team ()

## Notes

## Date: 23/05/2022 - current version as per market

| Environment - version | Market |
| ------ | ------ |
| test-cms1 AEM : 5.3.0-next | FR/ES/DE/IT |
| pre-cms1 AEM| DE(v5.1.0)/ES/IT/FR(v5.2.0) |

## Action for Pre-Prod

| Environment - version | Market | Status |
| ------ | ------ | ------ |
| Create PR for AEM | edit entity for PRE-live for all pages(product-list/product-detial/cart/checkout/brandteaser(v5.3.0-rc) | Done |
| pre-prod | all the market need point to v5.3 | Done |
| BFF - docker image for pre-prod |(PI22.1.3.3/ 11.4.3)-(23/05/2022) | Done |
| AWS | nothing to do|  nothing to do|
| Logs | |  |
| TROM | |  |

## Todo after prep-prod deployment for test-www

| Environment - version | Market | Status |
| ------ | ------ | ------ |
| Create PR for AEM | edit entity for NEXT for all pages(product-list/product-detial/cart/checkout/brandteaser(v5.4.0-Next) |  |
| test-cms1 | next go-live version example 5.4 (v11.5.0) |  |
