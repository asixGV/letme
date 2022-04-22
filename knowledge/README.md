# knowledge/dynamodb-structure.json
### _simple guide to understand the key-value pairs defined on the JSON document._

the JSON document is used on the DynamoDB service to centralize all the information about
your organization aws accounts. You can adapt, modify or create new keys which adjust to your 
business needs.
> note: remember that if you modify any key-value pairs you will need to also modify letme (shell script) to fetch them.

### Understanding the JSON keys/fields
| key | description|
| ------ | ------ |
| id | the id from the destination aws account. [AWS id guide](https://docs.aws.amazon.com/IAM/latest/UserGuide/console_account-alias.html) |
| name | name that letme will show when listing clients ``letme --list`` |
| url_qa | endpoints from the destination aws account which are related to the QA environment |
| k8s | name(s) of the k8s clusters from the destination account |
| tier | the account tier on your business model, premium, 8x5, basic... |
| url_sta | endpoints from the destination aws account which are related to the STAGING environment |
| role | the arn of the role that ``letme`` will assume to gain and store credentials |
| technologies | the name(s) of the technologies that the destination aws account uses |
| vcs_app | https or ssh command to download the application/code repository |
| vcs_inf | https or ssh command to download the infrastructure repository|
| region | first region specified is the main region, following regions are not used for production enviroments.|
| description | as the name implies, short description to summarize the destination aws account business plan... |
| url_pro | endpoints from the destination aws account which are related to the PRODUCTION environment (main website...) |
