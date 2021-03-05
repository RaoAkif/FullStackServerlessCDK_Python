## Step 01: Hello Lambda | FullStackServerlessCDK (Python)

#### Creating a Directory, and entring into it
```
mkdir hello-lambda
cd hello-lambda
or
mkdir hello-lambda && cd hello-lambda
```

#### Initiate CDK Template
```
cdk init app --language typescript
```

#### Add a Lambda Function
```
npm i @aws-cdk/aws-lambda @types/aws-lambda
```

#### Add an API Gateway
```
npm install @aws-cdk/aws-apigateway
```

In " lib/aws-cdk-typescript-stack.ts ", update your code (by importing lambda function and apigw)

```
import * as cdk from '@aws-cdk/core';
import * as lambda from '@aws-cdk/aws-lambda';
import * as apigw from '@aws-cdk/aws-apigateway';

export class Step01HelloLambdaStack extends cdk.Stack {
  constructor(scope: cdk.Construct, id: string, props?: cdk.StackProps) {
    super(scope, id, props);

    const hello = new lambda.Function(this, "HelloHandler", {
      runtime: lambda.Runtime.PYTHON_3_8,
      code: lambda.Code.fromAsset("lambda"),
      handler: "hello.handler",
    });

    new apigw.LambdaRestApi(this, "Endpoint", {
      handler: hello,
    });
    // The code that defines your stack goes here
  }
}

```

#### Create a Folder for Lambda Functions `lambda` and put a handler function for HelloLambda in `hello.ts`

```
def handler(event, context):
    print(event)

    return {
        "statusCode": 200,
        "headers": {
            "Content-Type": "text/plain"
        },
        "body": f"Hello, You've hit the path {event['path']}."
    }
```


#### Deploying the stack
```
cdk deploy
```

#### Destroy all Stacks
```
cdk destroy
```
