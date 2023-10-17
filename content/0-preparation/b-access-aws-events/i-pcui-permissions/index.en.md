---
title: "Update Parallel Cluster Lambda Role Permissions"
weight: 13
---

Be default AWS ParallelCluster API limits the policies you’re allowed to attach with AdditionalIAMPolicies to the following managed policies:

    arn:aws:iam::1234567890:policy/parallelcluster*
    arn:aws:iam::1234567890:policy/parallelcluster/*
    arn:aws:iam::aws:policy/CloudWatchAgentServerPolicy
    arn:aws:iam::aws:policy/AmazonSSMManagedInstanceCore
    arn:aws:iam::aws:policy/AWSBatchFullAccess
    arn:aws:iam::aws:policy/AmazonS3ReadOnlyAccess
    arn:aws:iam::aws:policy/service-role/AWSBatchServiceRole
    arn:aws:iam::aws:policy/service-role/AmazonEC2ContainerServiceforEC2Role
    arn:aws:iam::aws:policy/service-role/AmazonECSTaskExecutionRolePolicy
    arn:aws:iam::aws:policy/service-role/AmazonEC2SpotFleetTaggingRole
    arn:aws:iam::aws:policy/EC2InstanceProfileForImageBuilder
    arn:aws:iam::aws:policy/service-role/AWSLambdaBasicExecutionRole

If you try and attach a policy outside of this list, for example adding an ImportPath to the AWS Fsx for Lustre file system, you’ll get an error like:

![s3 ListBucket error](/static/images/0-pclusterui-s3-error.png)

To fix this, you can add additional IAM permissions to ParallelCluster UI like so:

1.  Go to the [Lambda Console (deeplink)](https://console.aws.amazon.com/lambda/home?#/functions?f0=true&fo=and&k0=functionName&n0=false&o0=%3A&op=and&v0=ParallelClusterFunction) and search for `ParallelClusterFunction`
2. Select the function then `Configuration` > `Permissions` > Click on the role under Role name.

![Parallel Cluster Lambda Role](/static/images/0-pclusterui-lambda-permissions.png)


3. Select the `AWSXRayDaemonWriteAccess` policy and remove it.

![Remove AWSXRayDaemonWriteAccess](/static/images/0-pclusterui-lambda-remove-xray.png)

4. Select `Add permissions` > Add Policies.

![Add Policies](/static/images/0-pclusterui-lambda-add-policy.png)

5. Add `AdministratorAccess` add `Save`.

![Add Administrator Access](/static/images/0-pclusterui-lambda-add-admin.png)


