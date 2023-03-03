# Welcome!
I'll provide Simple Template of AWS CodePipeline, which will be triggered by github commit events, and these cloudformation template.

## Prerequisite
---
- You have own AWS Account.
- You have Connected CodeBuild to Github by OAUTH or Github Access Token in your Work Region. If not, please follow the steps in this link. [link](https://docs.aws.amazon.com/codebuild/latest/userguide/access-tokens.html)
- You have Installed AWS CLI v2 on your laptop and set up is finished.

## Usage
---
- First, You must edit parameters/parameters_*.json files and change <> to your own parameters. For instance, next paragraph is parameters/parameters_codebuild.json.

~~~
[
    {
        "ParameterKey": "ArtifactBucketName",
        "ParameterValue": "<Your Artifact S3 Bucket Name>"
    },
    {
        "ParameterKey": "BuildProjectName",
        "ParameterValue": "<Build Project Name>"
    },
    {
        "ParameterKey": "SourceLocationURL",
        "ParameterValue": "https://github.com/<USER ID>/<REPOSITORY NAME>.git"
    }
]

~~~

- Deploy S3 Bucket (Optional)

~~~
 aws cloudformation --region <REGION> --stack-name <STACK-NAME> --template-file file://templates/template_s3bucket.yml --parameter-override file://parameters/parameters_s3bucket.yml
~~~

- Deploy Codebuild Project

~~~
 aws cloudformation --region <REGION> --stack-name <STACK-NAME> --template-file file://templates/template_codebuild.yml --parameter-override file://parameters/parameters_codebuild.json

~~~
