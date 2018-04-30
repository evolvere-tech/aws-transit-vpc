# Cloudformation Templates

The cloudformation templates in here are all unchanged apart from the transit transit-vpc-primary-account.template and the addition of the transit-vpc-stack-policy.json


## Cisco CSR Image Version

It is **imperative** that you use at least the 16.7 version if you are using private IP space starting with 192.168.x.x as there is a bug which prevents loading.

## Updates to CF Templates

Several changes have been made to the above mentioned template to enhance functionality. Additionally, the stack policy was also added to prevent users from making changes through CF to the CSR instances.

### New Input Parameters

- S3ConfiguratorBucket/Key, S3PollerBucket/Key have both been added to allow dynamic changes to the bucket where the code is stored for the lambda.

- CSRUsername and CSRPassword were added to facilitate adding usernames and passwords for static accounts
- CSRIngressCIDR was added to allow for a breakglass CIDR range to be added for access to the CSR CLI only

### CSR Specific Lambda
In order to allow more controlled scheduling of updates to the CSR's, 2 separate jobs were created in Lambda. This means that each has its own independent schedule via AWS Events cron, as well as its own permissions config. This must be maintained for the CF template to continue to work.

### S3 Bucket Permissions
Have been updated for the config bucket in order to allow the configurator lambdas to list and modify the contents of the bucket for batch processing purposes

### Send Anonymous Data

No! (This was set to no)

### Customisations to Cisco User Data
Specific updates were made to the userdata aspects of each of the CSR configs



