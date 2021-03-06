# Aliyun Function Compute Serverless Python Demo

## Getting started

This demo provides packaged services in the aliyun cloud market through Function Compute, such as free weather report, air quality report, and dressing index.
Invoke the demo function with city name(in chinese), it will return all the data of weather report and air quality report in JSON format.

### Pre-requisites

* Install Serverless CLI v1.26.1+. You can get it by running `npm i -g serverless`.
* An Aliyun account and open FunctionCompute service
* Activate the weather report service in the cloud market to get the app code in the console.

### Install demo & `serverless-aliyun-function-compute` plugin
You can install the demo from GitHub:

```sh
serverless install --url https://github.com/aliyun/serverless-function-compute-examples/tree/master/aliyun-python
```

The structure of the project should look something like this:

```
├── index.py
├── package.json
└── serverless.yml
```

Install `serverless-aliyun-function-compute` plugin to your service from https://github.com/aliyun/serverless-aliyun-function-compute

```sh
serverless plugin install --name serverless-aliyun-function-compute
```

### Prepare credential file
In order to deploy this function, we need the credentials with permissions to access Aliyun Function Compute.
Please create a `credentials` file and configure the credentials in it.
Here is an example `credentials` file:

```ini
[default]
aliyun_access_key_id = xxxxxxxx
aliyun_access_key_secret = xxxxxxxxxxxxxxxxxxxx
aliyun_account_id = 1234567890
```

You can find the `aliyun_access_key_secret` and `aliyun_access_key_id` from https://ak-console.aliyun.com/?#/accesskey . You can also choose to create an Access Key or use sub-account Access Key.
You can find the `aliyun_account_id` from https://account-intl.console.aliyun.com/?#/secure .
After creating the `aliyun_credentials` file, please make sure to change the `credentials` field value in `serverless.yml` to the absolute file path.

### Register and get your appcode

You can register and get your appcode from https://market.aliyun.com/products/57126001/cmapi014302.html . Then replace `<your app code>` with your code.

### Prepare input file

Please create a `event.json` file and copy the following content.

```json
{
    "city": "北京"
}
```

## Deploy and invoke
Make sure that you have activated Function Compute before attempting to deploy your function.

* Deploy your service to Aliyun:

  ```sh
  serverless deploy
  ```

* Invoke a function directly (without going through the API gateway):

  ```sh
  serverless invoke --function weather --path event.json
  ```

* Get information on your deployed functions

  ```sh
  serverless info
  ```

* When you no longer needs your service, you can remove the service, functions, along with deployed endpoints and triggers using:

  ```sh
  serverless remove
  ```
