# letme (open-source)
### _gain cross-account short-term aws credentials._

`letme` is a simple bash script that enables the source user to interact with multiple
aws accounts through the aws command line interface (aws-cli) using the `--profile` argument and using a DynamoDB to centralize information.

### Requirements:
- access to an AWS account.
- a DynamoDB table (located on the 'main' account) with a pre-defined structure (check `/knowledge/dynamodb-structure.json`)
- a trusted iam role on accounts each that need to be accessed. 
- unix based system supporting bash version 3.2.57 or above
- script dependencies ([jq], [aws-cli], [sed])
> Note: we endorse reading the following guides to better understand the needs of `letme`
### Official AWS guides:
- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html
- https://aws.amazon.com/premiumsupport/knowledge-center/iam-assume-role-cli/?nc1=h_ls
- https://aws.amazon.com/es/blogs/security/how-to-use-trust-policies-with-iam-roles/
* * *
### Installing letme
There are two ways of installing `letme`:
##### _directly from github:_
- download source code:
```sh
git clone https://github.com/lockedinspace/letme.git
```
- provide script execute permissions and move to any $PATH directory:
```sh
chmod 755 /src/letme
mv /src/letme $PATH
```
##### _directly from brainer:_
work in progress.
> Note: be sure to clean up any unwanted files once you have installed and configured everything.
* * *
### Setting up letme
   [jq]: <https://github.com/stedolan/jq>
   [aws-cli]: <https://github.com/aws/aws-cli>
   [sed]: <https://linux.die.net/man/1/sed>


