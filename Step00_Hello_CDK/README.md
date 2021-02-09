## Step 1: Hello CDK | FullStackServerlessCDK (Python)

#### Creating a Directory, and entring into it
```
mkdir hello-cdk
cd hello-cdk
or
mkdir hello-cdk && cd hello-cdk
```

#### Initiate CDK Template
```
cdk init app --language python
```

After the template has been created, Activate the this app's Python virtual environment and install its dependencies

```
python3 -m venv my-venv
```
my-venv folder will be created 
To activate your venv
```
my-venv\Scripts\activate
```

#### Add an Amazon Bucket
```
pip install aws-cdk.aws-s3
```

In " aws_cdk_python/aws_cdk_python_stack.py ", update your code (by importing s3 bucket and creating a new s3 bucket)


```
from aws_cdk import (
    aws_s3 as s3,
    core
)


class AwsCdkPythonStack(core.Stack):

    def __init__(self, scope: core.Construct, construct_id: str, **kwargs) -> None:
        super().__init__(scope, construct_id, **kwargs)

        bucket = s3.Bucket(self, 
    "MyBootcampBucket", 
    versioned=True,)```


#### Deploying the stack
```
cdk deploy
```

#### Destroy all Stacks
```
cdk destroy
```
