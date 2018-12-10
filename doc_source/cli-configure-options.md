# Command Line Options<a name="cli-configure-options"></a>

You can use the following command line options to override the default configuration settings for a single command\. You cannot use command line options to directly specify credentials, although you can specify which profile to use\.

**\-\-profile**  
Specifies the [named profile](cli-configure-profiles.md) to use for this command\. To set up additional named profiles, you can use the `aws configure` command with the `--profile` option\.  

```
$ aws configure --profile <profilename>
```

**\-\-region**  
Specifies which AWS region to send this command's AWS request to\. For a list of all of the regions that you can specify, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the Amazon Web Services General Reference\.

**\-\-output**  
Specifies the output format to use for this command\. You can specify any of the following values:  
+ **`json`**: The output is formatted as a [JSON](https://json.org/) string\.
+ **`text`**: The output is formatted as multiple lines of tab\-separated string values which can be useful if you want to pass the output to a text processor, like `grep`, `sed`, or `awk`\.
+ **`table`**: The output is formatted as a table using the characters \+\|\- to form the cell borders\. It typically presents the information in a "human\-friendly" format that is much easier to read than the others, but not as programmatically useful\.

**\-\-endpoint\-url**  
The URL to send the request to\. For most commands, the AWS CLI automatically determines the URL based on the selected service and the specified AWS region\. However, some commands require that you specify an account\-specific URL\. You can also configure some AWS services to [host an endpoint directly within your private VPC](https://docs.aws.amazon.com/vpc/latest/userguide/what-is-amazon-vpc.html#what-is-privatelink), which might then need to be specified\.   
For a list of the standard service endpoints available in each region, see [AWS Regions and Endpoints](https://docs.aws.amazon.com/general/latest/gr/rande.html) in the Amazon Web Services General Reference\.

When you provide one or more of these options as command line parameters, it overrides the default configuration or any corresponding profile setting for that single command\. Each option takes a string argument with a space or equals sign \(=\) separating the argument from the option name\. If the argument value contains a space, then you must use quotation marks around the argument\.

Common uses for command line options include checking your resources in multiple AWS Regions, and changing the output format for legibility or ease of use when scripting\. For example, if you're not sure which region your instance is running in, you can run the **describe\-instances** command against each region until you find it, as follows\. 

```
$ aws ec2 describe-instances --output table --region us-east-1
-------------------
|DescribeInstances|
+-----------------+
$ aws ec2 describe-instances --output table --region us-west-1
-------------------
|DescribeInstances|
+-----------------+
$ aws ec2 describe-instances --output table --region us-west-2
------------------------------------------------------------------------------
|                              DescribeInstances                             |
+----------------------------------------------------------------------------+
||                               Reservations                               ||
|+-------------------------------------+------------------------------------+|
||  OwnerId                            |  012345678901                      ||
||  ReservationId                      |  r-abcdefgh                        ||
|+-------------------------------------+------------------------------------+|
|||                                Instances                               |||
||+------------------------+-----------------------------------------------+||
|||  AmiLaunchIndex        |  0                                            |||
|||  Architecture          |  x86_64                                       |||
...
```

The argument types \(string, Boolean, etc\.\) for each command line option are described in detail in [Specifying Parameter Values](cli-using-param.md)\.