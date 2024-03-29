# letme
### _gain cross-account short-term aws credentials._

`letme` is a simple bash script that enables the source user to interact with multiple
aws accounts through the aws command line interface (aws-cli) using the `--profile` argument and centralizing the information on a DynamoDB table.
To have a better understanding, think of the DynamoDB table as an API that is requested by `letme` and the result is shown to the end user.

### What ``letme`` offers to the end user:
- secure MFA authentication when requesting credentials (can be disabled).
- lowering your aws billing with the ``--init`` (creates a local cache to reduce calls made to AWS).
- multi account management through the ``--profile`` argument (aws-cli argument).
- made purely with bash (with some external script dependencies, check [Requirements](#requirements)).
- centralize all your information and mantain a clean organization (DynamoDB table).
- easily modify this script and the json table structure and adapt to your specific needs.
- portable through BSD and GNU userlands.

### Requirements:
- access to an AWS account.
- a DynamoDB table (located on the 'main' account) with a pre-defined structure (check `/knowledge/dynamodb-structure.json`)
- a trusted iam role on each account that need to be accessed. 
- unix based system supporting bash version 3.2.57 or above
- script dependencies ([jq], [aws-cli], [sed])
> note: we endorse reading the following guides to better understand the needs of `letme`
### Official AWS guides:
- https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html
- https://aws.amazon.com/premiumsupport/knowledge-center/iam-assume-role-cli/?nc1=h_ls
- https://aws.amazon.com/es/blogs/security/how-to-use-trust-policies-with-iam-roles/
* * *
### Installing letme
##### _directly from github:_
- download source code:
```sh
git clone https://github.com/lockedinspace/letme.git
```
- provide script execute permissions and move to the first $PATH variable directory:
```sh
#get the first directory from the $PATH variable.
var=$(echo $PATH | awk -F':' '{print $1}')
#provide execute permissions to letme
chmod 755 letme/src/letme
#move letme script to the first path from the $PATH variable.
mv -f letme/src/letme $var
```
> note: be sure to clean up any unwanted files once you have installed and configured everything.
* * *
### Setting up letme
- check if letme is installed correctly.
```sh
sudo letme --help
```
   [jq]: <https://github.com/stedolan/jq>
   [aws-cli]: <https://github.com/aws/aws-cli>
   [sed]: <https://linux.die.net/man/1/sed>
* * *
### Troubleshooting
```sh
$ sudo letme --list

An error occurred (ResourceNotFoundException) when calling the Scan operation: Requested resource not found
ERROR: could not connect to DynamoDB.
```
- Please check the region being setted on the default profile is the same where DynamoDB table is stored. (~/.aws/config)

