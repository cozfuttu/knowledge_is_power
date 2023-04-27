1) Login as root user, then open [IAM Console](https://console.aws.amazon.com/iam/)
2) Click Users on the left, then click Add Users
3) If you want only programmatic access, do not check the "Enable console access" checkbox. If you check it, then the user is able to login through AWS Console. Then, click "Next".
4) Click "Attach Policies Directly", then choose the [policies](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#access_policy-types) you want to attach to the user. Click Next.
5) Click "Create User". If you want the user to have programmatic access, you need to generate an access key and a secret access key. To generate them, click the user, then click the "Security Credentials" tab.
6) Scroll down and find "Create access key" under the "Access keys" section. Choose the option you need (probably CLI), check the box and click "Next".
7) Click "Create Access Key". 