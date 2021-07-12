# aws-cdk-demo
TLDR: easy to use, but lacking many python examples (although the most important services are covered, except batch). API doc examples are in Typescript so conversion to python is necessary. Possibly good work for a contrtactor

AWS Cloud Development Kit (AWS CDK) lets you define your cloud infrastructure as code in one of five supported programming languages, including Python. The output of an AWS CDK program is a AWS CloudFormation template.

An AWS CDK app in Python uses the AWS CDK to define AWS infrastructure. An app defines one or more stacks. Stacks (equivalent to AWS CloudFormation stacks) contain constructs, each of which defines one or more concrete AWS resources, such as Amazon S3 buckets, Lambda functions, Amazon DynamoDB tables, and so on.

Example:
```python
bucket = s3.Bucket(self, "MyBucket", bucket_name="my-bucket", versioned=True,
            website_redirect=s3.RedirectTarget(host_name="aws.amazon.com"))
```

Install the CDK `$ sudo npm install -g aws-cdk` and verify with `cdk --version`. Now work through [Your first AWS CDK app](https://docs.aws.amazon.com/cdk/latest/guide/hello_world.html). Remember to `cdk destroy` at end

Note: Each AWS CDK app should be in its own directory, with its own local module dependencies.

## Workflow for new app
Steps for the `hello-cdk` example:
- `mkdir hello-cdk`
- `cd hello-cdk`
- `cdk init app --language python`
- `source .venv/bin/activate`
- `python -m pip install -r requirements.txt`
- edit `app.py`
- `cdk synth` to Synthesize an AWS CloudFormation template for the app
- `cdk deploy`/`cdk diff`/`cdk destroy` as required

## CICD
A [github action](https://github.com/marketplace/actions/aws-cdk-github-actions) is documented and tested, but currently disabled since it is anticipated that infrastructure upgrades will be performed manually in the immediate future.

## Resources
- https://docs.aws.amazon.com/cdk/latest/guide/getting_started.html
- https://github.com/marketplace/actions/aws-cdk-github-actions
- https://github.com/aws-samples/aws-cdk-examples
- https://docs.aws.amazon.com/cdk/api/latest
