---
title: HashiCorp Vault
date: 2020-06-10T22:15:00.000Z
description: Getting Started Guide
---
# HashiCorp Vault

## Installing Vault

- Chocolatey on Windows

    ```cmd
    choco install vault
    ```

- Manual Installation

    After downloading Vault, unzip the package. Vault runs as a single binary named vault. Any other files in the package can be safely removed and Vault will still function.

    <https://www.vaultproject.io/downloads>

- The final step is to make sure that the vault binary is available on the PATH

## Verify the installation

Open a new terminal session and checking that the vault binary is available. By executing vault, you should see help output similar to the following:

```pwsh
PS C:\Users\Ashish> vault
Usage: vault <command> [args]

Common commands:
    read        Read data and retrieves secrets
    write       Write data, configuration, and secrets
    delete      Delete secrets and configuration
    list        List data or secrets
    login       Authenticate locally
    agent       Start a Vault agent
    server      Start a Vault server
    status      Print seal and HA status
    unwrap      Unwrap a wrapped secret

Other commands:
    audit          Interact with audit devices
    auth           Interact with auth methods
    debug          Runs the debug command
    kv             Interact with Vault's Key-Value storage
    lease          Interact with leases
    namespace      Interact with namespaces
    operator       Perform operator-specific tasks
    path-help      Retrieve API help for paths
    plugin         Interact with Vault plugins and catalog
    policy         Interact with policies
    print          Prints runtime configurations
    secrets        Interact with secrets engines
    ssh            Initiate an SSH session
    token          Interact with tokens
PS C:\Users\Ashish>
```

## Advanced shell configuration

### Command Completion

```pwsh
vault -autocomplete-install
```

## Starting the DevServer

Vault operates as a client/server application. The Vault server is the only piece of the Vault architecture that interacts with the data storage and backends. All operations done via the Vault CLI interact with the server over a TLS connection.

### Starting the Dev Server 

First, start a Vault dev server. The dev server is a built-in, pre-configured server that is not very secure but useful for playing with Vault locally.

```pwsh
vault server -dev

...
The unseal key and root token are displayed below in case you want to
seal/unseal the Vault or re-authenticate.

Unseal Key: XSOpPJLLZsA9kkdZBtcYmuStaFSFK46zDO8AiGs6DvA=
Root Token: s.whfS6Rfp7sw2DWw1skHpVAaM

Development mode should NOT be used in production installations!
...

```

Notice that Unseal Key and Root Token values are displayed.

>The dev server stores all its data in-memory (but still encrypted), listens on localhost without TLS, and automatically unseals and shows you the unseal key and root access key.

PowerShell :

```pwsh
$Env:VAULT_ADDR = "http://127.0.0.1:8200"
# VAULT_ADDR will configure the Vault client to talk to our dev server

$Env:VAULT_DEV_ROOT_TOKEN_ID  = "s.whfS6Rfp7sw2DWw1skHpVAaM"
# Setting this environment variable is a way to provide the token to Vault.
```

### Verify the Server is Running

```pwsh
vault status
```

## Your First Secret

One of the core features of Vault is the ability to read and write arbitrary secrets securely.

We will use the CLI, but there is also a complete HTTP API that can be used to programmatically do anything with Vault.

Secrets written to Vault are encrypted and then written to backend storage. For our dev server, backend storage is in-memory, but in production this would more likely be on disk or in Consul. Vault encrypts the value before it is ever handed to the storage driver. The backend storage mechanism never sees the unencrypted value and doesn't have the means necessary to decrypt it without Vault.

### Writing a Secret

vault kv command

```pwsh
vault kv put secret/hello foo=world
```

This writes the pair foo=world to the path secret/hello. 

For now it is important that the path is prefixed with secret/, otherwise this example won't work. The secret/ prefix is where arbitrary secrets can be read and written.

You can even write multiple pieces of data.

```pwsh
vault kv put secret/hello foo=world excited=yes
```

The vault kv command interacts with K/V secrets engines.

> Warning: The examples in this guide use the ```<key>=<value>``` input to send secrets to Vault. However, sending data as    a part of the CLI command often end up in the shell history unencrypted. To avoid this, refer to the [documentation](https://www.vaultproject.io/docs/commands#writing-data) or [Static Secrets: Key/Value Secrets Engine guide](https://learn.hashicorp.com/vault/secrets-management/sm-static-secrets#additional-discussion) to learn different approaches.

### Getting a Secret

secrets can be retrieved with ```vault kv get```

```pwsh
vault kv get secret/hello
```

Vault gets the data from storage and decrypts it. The output format is purposefully whitespace separated to make it easy to pipe into a tool like awk.

This contains some extra information. To print only the value of a given field, use the -field=<key_name> flag.

```pwsh
vault kv get -field=excited secret/hello
```

Optional JSON output is very useful for scripts. For example, you can use the jq tool to extract the value of the excited secret.

```pwsh
vault kv get -format=json secret/hello

# jq Works in bash
# vault kv get -format=json secret/hello | jq -r .data.data.excited
```

### Deleting a Secret

delete a secret using the vault kv delete command.

```bash
vault kv delete secret/hello
```

We used powerful CRUD features of Vault to store arbitrary secrets. On its own, this is already a useful but basic feature.

## Secret Engines

Vault behaves similarly to a virtual filesystem. The read/write/delete/list operations are forwarded to the corresponding secrets engine, and the secrets engine decides how to react to those operations.

Notice all requests started with ```secret/``` while creating arbitary secrets

The path prefix tells Vault which secrets engine to which it should route traffic. When a request comes to Vault, it matches the initial path part using a longest prefix match and then passes the request to the corresponding secrets engine enabled at that path. Vault presents these secrets engines similar to a filesystem.

By default, Vault enables Key/Value version2 secrets engine (kv-v2) at the path secret/ when running in dev mode. The key/value secrets engine reads and writes raw data to the backend storage. Vault supports many other secrets engines, and this feature makes Vault flexible and unique.

>NOTE: The key/value secrets engine has two versions: ```kv``` (version 1) and ```kv-v2``` (version 2). The ```kv-v2``` is versioned ```kv``` secrets engine which can retain a number of secrets versions.

### Enable a Secrets Engine

To get started, we will enable the kv secrets engine. Each path is completely isolated and cannot talk to other paths.

```pwsh
vault secrets enable -path=kv kv
```

The path where the secrets engine is enabled defaults to the name of the secrets engine.

Thus, the following command is equivalent to executing the above command.

```pwsh
vault secrets enable kv
```

To verify our success and get more information about the secrets engine, use the vault secrets list command:

```pwsh
vault secrets list
```

This shows there are 4 enabled secrets engines on this Vault server. You can see the type of the secrets engine, the corresponding path, and an optional description (or "n/a" if none was given).

>The ```sys/``` path corresponds to the system backend. These paths interact with Vault's core system and are not required for beginners.

```pwsh
vault kv put kv/hello target=world
```

To read the secrets stored in the ```kv/hello``` path, use the ```kv get``` command.

```pwsh
vault kv get kv/hello
```

List existing keys at the ```kv``` path.

```pwsh
vault kv list kv/
```

### Disable a Secrets Engine

When a secrets engine is no longer needed, it can be disabled. When a secrets engine is disabled, all secrets are revoked and the corresponding Vault data and configuration is removed.

```pwsh
vault secrets disable kv/
```

Note that this command takes a PATH to the secrets engine as an argument, not the TYPE of the secrets engine.

Any requests to route data to the original path would result in an error, but another secrets engine could now be enabled at that path.

## Dynamic Secrets

### Enable AWS Secrets engine

```pwsh
vault secrets enable -path=aws aws
```

### Configure the AWS secrets engine

After enabling the AWS secrets engine, you must configure it to authenticate and communicate with AWS. This requires privileged account credentials. If you are unfamiliar with AWS, use your root account keys.

> Warning: Do not use your root account keys in production. This is a getting started guide and is not a best practices guide for production installations.

```pwsh
vault write aws/config/root \
    access_key=AKIAI4SGLQPBX6CSENIQ \
    secret_key=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 \
    region=us-east-1

Success! Data written to: aws/config/root
```

These credentials are now stored in this AWS secrets engine. The engine will use these credentials when communicating with AWS in future requests.

### Create a role

The next step is to configure a role. Vault knows how to create an IAM user via the AWS API, but it does not know what permissions, groups, and policies you want to attach to that user. This is where roles come in - a role in Vault is a human-friendly identifier to an action.

For example, here is an IAM policy that enables all actions on EC2, but not IAM or other AWS services.

```pwsh
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1426528957000",
      "Effect": "Allow",
      "Action": ["ec2:*"],
      "Resource": ["*"]
    }
  ]
}
```

> NOTE: If you are not familiar with AWS' IAM policies, that is okay - just use this one for now.

We need to map this policy document to a named role. To do that, write to ```aws/roles/:name``` where ```:name``` is your unique name that describes the role (such as ```aws/roles/my-role```):

```pwsh
vault write aws/roles/my-role \
        credential_type=iam_user \
        policy_document=-<<EOF
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1426528957000",
      "Effect": "Allow",
      "Action": [
        "ec2:*"
      ],
      "Resource": [
        "*"
      ]
    }
  ]
}
EOF
Success! Data written to: aws/roles/my-role
```

We just told Vault:

>When I ask for a credential for "my-role", create it and attach the IAM policy { "Version": "2012..." }.

### Generate the secret

Now that the AWS secrets engine is enabled and configured with a role, we can ask Vault to generate an access key pair for that role by reading from ```aws/creds/:name```, where ```:name``` corresponds to the name of an existing role:

```pwsh
vault read aws/creds/my-role

Key                Value
---                -----
lease_id           aws/creds/my-role/0bce0782-32aa-25ec-f61d-c026ff22106e
lease_duration     768h
lease_renewable    true
access_key         AKIAJELUDIANQGRXCTZQ
secret_key         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
security_token     <nil>
```

Success! The access and secret key can now be used to perform any EC2 operations within AWS.

Notice that these keys are new, they are not the keys you entered earlier. If you were to run the command a second time, you would get a new access key pair. Each time you read from aws/creds/:name, Vault will connect to AWS and generate a new IAM user and key pair.

Copy the full path of this ```lease_id``` value found in the output. This value is used for renewal, revocation, and inspection.

### Revoke the secret

Vault will automatically revoke this credential after 768 hours (see ```lease_duration``` in the output), but perhaps we want to revoke it early. Once the secret is revoked, the access keys are no longer valid.

To revoke the secret, use ```vault revoke``` with the lease ID that was outputted from ```vault read`` when you ran it:

```pwsh
vault lease revoke aws/creds/my-role/0bce0782-32aa-25ec-f61d-c026ff22106

Success! Revoked lease: aws/creds/my-role/0bce0782-32aa-25ec-f61d-c026ff22106e
```

Done! If you login to your AWS account, you will see that no IAM users exist. If you try to use the access keys that were generated, you will find that they no longer work.

## Built-in Help

Instead of having to memorize or reference documentation constantly to determine what paths to use, Vault has a built-in help system.

This help system can be accessed via the API or the command-line and generates human-readable help for any path.

### Secrets Engines Overview

This section assumes you have the AWS secrets engine enabled at ```aws/```. If you do not, enable it before continuing:

```pwsh
vault secrets enable -path=aws aws
```

With the secrets engine enabled, learn about it with the ```vault path-help``` command:

```pwsh
vault path-help aws

### DESCRIPTION

The AWS backend dynamically generates AWS access keys for a set of
IAM policies. The AWS access keys have a configurable lease set and
are automatically revoked at the end of the lease.

After mounting this backend, credentials to generate IAM keys must
be configured with the "root" path and policies must be written using
the "roles/" endpoints before any access keys can be generated.

### PATHS

The following paths are supported by this backend. To view help for
any of the paths below, use the help command with any route matching
the path pattern. Note that depending on the policy of your auth token,
you may or may not be able to access certain paths.

    ^config/lease$
        Configure the default lease information for generated credentials.

    ^config/root$
        Configure the root credentials that are used to manage IAM.

    ^creds/(?P<name>\w+)$
        Generate an access key pair for a specific role.

    ^roles/(?P<name>\w+)$
        Read and write IAM policies that access keys can be made for.
```

The ```vault path-help``` command takes a path. By specifying a root path, it will give us the overview of that secrets engine. Notice how the help not only contains a description, but also the exact regular expressions used to match routes for this backend along with a brief description of what the route is for.

### Path Help

After seeing the overview, we can continue to dive deeper by getting help for an individual path. For this, just use ```vault path-help``` with a path that would match the regular expression for that path. Note that the path doesn't need to actually work. For example, we'll get the help below for accessing ```aws/creds/my-non-existent-role```, even though we never created the role:

```pwsh
vault path-help aws/creds/my-non-existent-role

Request:        creds/my-non-existent-role
Matching Route: ^creds/(?P<name>\w(([\w-.]+)?\w)?)$

Generate an access key pair for a specific role.

### PARAMETERS

    name (string)
        Name of the role

### DESCRIPTION

This path will generate a new, never before used key pair for
accessing AWS. The IAM policy used to back this key pair will be
the "name" parameter. For example, if this backend is mounted at "aws",
then "aws/creds/deploy" would generate access keys for the "deploy" role.

The access keys will have a lease associated with them. The access keys
can be revoked by using the lease ID.
```

Within a path, we are given the parameters that this path requires. Some parameters come from the route itself. In this case, the name parameter is a named capture from the route regular expression. There is also a description of what that path does.

Go ahead and explore more paths! Enable other secrets engines, traverse their help systems, and learn about what they do.

The help system lets you learn about how to use any backend within Vault without leaving the command line.

## Authentication

Now we will explore authentication with Vault tokens and GitHub credentials.

### Token authentication

Token authentication is automatically enabled. When you started the dev server, the output displayed a _root token_. The Vault CLI read the _root token_ from the ```$VAULT_DEV_ROOT_TOKEN_ID``` environment variable. This root token can perform any operation within Vault because it is assigned the root policy. One capability is to create new tokens.

```pwsh
vault token create

Key                  Value
---                  -----
token                s.iyNUhq8Ov4hIAx6snw5mB2nL
token_accessor       maMfHsZfwLB6fi18Zenj3qh6
token_duration       ∞
token_renewable      false
token_policies       ["root"]
identity_policies    []
policies             ["root"]
```

The token is created and the output describes this token a table of keys and values. The created ```token``` is displayed here as ```s.iyNUhq8Ov4hIAx6snw5mB2nL```.

This token is a child of the root token, and by default, it inherits the policies from its parent.

Login with this new token.

```pwsh
vault login s.iyNUhq8Ov4hIAx6snw5mB2nL

Success! You are now authenticated. The token information displayed below
is already stored in the token helper. You do NOT need to run "vault login"
again. Future Vault requests will automatically use this token.

Key                  Value
---                  -----
token                s.iyNUhq8Ov4hIAx6snw5mB2nL
token_accessor       maMfHsZfwLB6fi18Zenj3qh6
token_duration       ∞
token_renewable      false
token_policies       ["root"]
identity_policies    []
policies             ["root"]

```

You successfully authenticated with this new token. As this token has the root policy it can create its own tokens.

```pwsh
vault token create

Key                  Value
---                  -----
token                s.TsKT5ubouZ7TF26Eg7wNIl3k
token_accessor       b1d0curWHYqmgCndk0G1cM6R
token_duration       ∞
token_renewable      false
token_policies       ["root"]
identity_policies    []
policies             ["root"]
```

The token is created and displayed here as ```s.TsKT5ubouZ7TF26Eg7wNIl3k```. Each token that Vault creates is unique.

When a token is no longer needed it can be revoked.

Revoke the first token you created.

```pwsh
vault token revoke s.iyNUhq8Ov4hIAx6snw5mB2nL

Success! Revoked token (if it existed)
```

The token has been revoked.

Attempt to login with the last token you created.

```pwsh
vault login s.TsKT5ubouZ7TF26Eg7wNIl3k
Error authenticating: error looking up token: Error making API request.

URL: GET http://127.0.0.1:8200/v1/auth/token/lookup-self
Code: 403. Errors:

* permission denied
```

You are not able to authenticate with this token because when a token is revoked it will revoke all the tokens that it created.

Login with the root token.

```pwsh
vault login $VAULT_DEV_ROOT_TOKEN_ID
```

You successfully authenticated again with the root token.

### GitHub authentication

Vault supports authentication methods for human operators. GitHub authentication enables a user to authenticate with Vault by providing their GitHub credentials and receive a Vault token.

NOTE: This authentication method, as described in the exercises, requires that you have a GitHub profile, belong to a team in a GitHub organization, and have generated a GitHub access token with the read:org scope.

Enable the GitHub auth method.

```pwsh
vault auth enable github

Success! Enabled github auth method at: github/
```

The auth method is enabled and available at the path ```auth/github/```.

This auth method requires that you set a GitHub organization in the configuration. A GitHub organization maintains a list of users which you are allowing to authenticate with Vault.

Set the ```organization``` for the ```github``` authentication.

```pwsh
vault write auth/github/config organization=hashicorp
```

Now all users within the ```hashicorp``` GitHub organization are able to authenticate.

GitHub organizations can define teams. Each team may have access to different actions across all the repositories that the organization maintains. These teams may also need access to specific secrets within Vault.

Configure the GitHub ```engineering``` team authentication to be granted the ```default``` and ```applications``` policies.

```pwsh
vault write auth/github/map/teams/engineering value=default,applications

Success! Data written to: auth/github/map/teams/engineering
```

The members of the GitHub ```engineering``` team in the ```hashicorp``` organization will authenticate and are authorized with the ```default``` and ```applications``` policies.

> NOTE: The applications policy is not yet defined in Vault. Vault still allows users to authenticate but produces a warning until that policy is defined.

Display all the authentication methods that Vault has enabled.

```pwsh
vault auth list

Path       Type      Description
----       ----      -----------
github/    github    n/a
token/     token     token based credentials
```

The output displays the ```github``` and ```token``` auth methods.

earn more about the github auth method using ```help```.

```pwsh
vault auth help github

Usage: vault login -method=github [CONFIG K=V...]

  The GitHub auth method allows users to authenticate using a GitHub
  personal access token. Users can generate a personal access token from the
  settings page on their GitHub account.

  Authenticate using a GitHub token:

      $ vault login -method=github token=abcd1234

## ...
```

The output displays an example of login with the github method. This method requires that the method be defined and that an operator provide a [GitHub personal access token](https://help.github.com/en/github/authenticating-to-github/creating-a-personal-access-token-for-the-command-line).

```pwsh
vault login -method=github

GitHub Personal Access Token (will be hidden):
Success! You are now authenticated. The token information displayed below
is already stored in the token helper. You do NOT need to run "vault login"
again. Future Vault requests will automatically use this token.

Key                    Value
---                    -----
token                  s.DNtKCjVQ1TxAzgMqtDuwjjC2
token_accessor         e7zLJuPg2tLpav66ZSu5AyDC
token_duration         768h
token_renewable        true
token_policies         [default applications]
token_meta_org         hashicorp
token_meta_username    my-user
```

When the GitHub personal access token is not provided to the command the Vault CLI prompts the operator. If a valid GitHub personal access token is provided then the operator logs in and the output displays a Vault token. The operator can use the Vault token until it is revoked or its lifetime exceeds the ```token_duration```.

Login with the root token.

```pwsh
vault login $VAULT_DEV_ROOT_TOKEN_ID
```

Revoke all tokens generated the ```github``` auth method.

```pwsh
vault token revoke -mode path auth/github
```

All tokens generated by logins to the path ```auth/github``` are revoked.

All authentication methods, except for the token auth method, can be disabled.

```pwsh
Display the github auth method.

vault auth disable github

Success! Disabled the auth method (if it existed) at: github/
```

All tokens generated by logins using this authentication method are revoked.

## Policies

Policies in Vault control what a user can access. In the last section, we learned about ```authentication```. This section is about ```authorization```.

For authentication Vault has multiple options or methods that can be enabled and used. Vault always uses the same format for both authorization and policies. All auth methods map identities back to the core policies that are configured with Vault.

There are some built-in policies that cannot be removed. For example, the ```root``` and ```default``` policies are required policies and cannot be deleted. The ```default``` policy provides a common set of permissions and is included on all tokens by default. The ```root``` policy gives a token super admin permissions, similar to a root user on a linux machine.

### Policy Format

Policies are authored in [HCL](https://github.com/hashicorp/hcl), but are JSON compatible. Here is an example policy:

```pwsh
# Dev servers have version 2 of KV secrets engine mounted by default, so will
# need these paths to grant permissions:
path "secret/data/*" {
  capabilities = ["create", "update"]
}

path "secret/data/foo" {
  capabilities = ["read"]
}
```

With this policy, a user could write any secret to ```secret/data/```, except to ```secret/data/foo```, where only read access is allowed. Policies default to deny, so any access to an unspecified path is not allowed.

Do not worry about getting the exact policy format correct. Vault includes a command that will format the policy automatically according to specification. It also reports on any syntax errors.

```pwsh
vault policy fmt my-policy.hcl
```

The policy format uses a prefix matching system on the API path to determine access control. The most specific defined policy is used, either an exact match or the longest-prefix glob match. Since everything in Vault must be accessed via the API, this gives strict control over every aspect of Vault, including enabling secrets engines, enabling auth methods, authenticating, as well as secret access.

### Writing the Policy

To write a policy using the command line, specify the path to a policy file to upload.

```pwsh
vault policy write my-policy my-policy.hcl
```

Here is an example you can copy-paste in the terminal.

```pwsh
vault policy write my-policy -<<EOF
# Dev servers have version 2 of KV secrets engine mounted by default, so will
# need these paths to grant permissions:
path "secret/data/*" {
  capabilities = ["create", "update"]
}

path "secret/data/foo" {
  capabilities = ["read"]
}
EOF
```

To see the list of policies, execute the following command.

```pwsh
vault policy list

default
my-policy
root
```

To view the contents of a policy, execute the vault policy read command.

```pwsh
vault policy read my-policy

# Dev servers have version 2 of KV secrets engine mounted by default, so will
# need these paths to grant permissions:
path "secret/data/*" {
  capabilities = ["create", "update"]
}

path "secret/data/foo" {
  capabilities = ["read"]
}
```

### Testing the Policy

First, check to verify that KV v2 secrets engine has not been enabled at ```secret/```.

```pwsh
vault secrets list
```

If secret/ is not listed, enable it before proceeding.

```pwsh
vault secrets enable -path=secret/ kv-v2
```

To use the policy, create a token and assign it to that policy.

```pwsh
vault token create -policy=my-policy

Key                  Value
---                  -----
token                s.X6gvFko7chPilgV0lpWXsdeu
token_accessor       kwgaMv7lz09a5oULHIT3UQ6z
token_duration       768h
token_renewable      true
token_policies       ["default" "my-policy"]
identity_policies    []
policies             ["default" "my-policy"]
```

Copy the generated token value and authenticate with Vault.

```pwsh
vault login s.X6gvFko7chPilgV0lpWXsdeu

Success! You are now authenticated. The token information displayed below
is already stored in the token helper. You do NOT need to run "vault login"
again. Future Vault requests will automatically use this token.

Key                  Value
---                  -----
token                s.X6gvFko7chPilgV0lpWXsdeu
token_accessor       kwgaMv7lz09a5oULHIT3UQ6z
token_duration       767h59m40s
token_renewable      true
token_policies       ["default" "my-policy"]
identity_policies    []
policies             ["default" "my-policy"]
```

Verify that you can write any data to ```secret/data/```.

>NOTE: When you access the [KV v2 secrets engine](https://www.vaultproject.io/docs/secrets/kv/kv-v2) using the ```vault kv``` CLI commands, you can omit /data in the secret path.

```pwsh
vault kv put secret/creds password="my-long-password"

Key              Value
---              -----
created_time     2018-05-22T18:05:42.537496856Z
deletion_time    n/a
destroyed        false
version          1
```

Since my-policy only permits read from the ```secret/data/foo``` path, any attempt to write fails with "permission denied" error.

```pwsh
vault kv put secret/foo robot=beepboop

Error writing data to secret/data/foo: Error making API request.

URL: PUT http://127.0.0.1:8200/v1/secret/data/foo
Code: 403. Errors:

* permission denied
```

You also do not have access to ```sys``` according to the policy, so commands like vault policy list or vault secrets list will not work.

You also do not have access to sys according to the policy, so commands like ```vault policy list``` or ```vault secrets list``` will not work.

Re-authenticate with the initial root token to continue.

```pwsh
vault login $VAULT_DEV_ROOT_TOKEN_ID
```

### Mapping Policies to Auth Methods

Vault itself is the single policy authority, unlike authentication where you can enable multiple auth methods. Any enabled auth method must map identities to these core policies.

Use the vault path-help system with your auth method to determine how the mapping is done since it is specific to each auth method. For example, with GitHub, it is done per team using the ```map/teams/<team>``` path.

```pwsh
vault write auth/github/map/teams/default value=my-policy

Success! Data written to: auth/github/map/teams/default
```

For GitHub, the ```default``` team is the default policy set that everyone is assigned to no matter what team they're on.

Other auth methods use alternate, but likely similar mechanisms for mapping policies to identity.

Policies are an important part of Vault. While using the root token is easiest to get up and running, you will want to restrict access to Vault very quickly, and the policy system is the way to do this.

The syntax and function of policies is easy to understand and work with, and because auth methods all must map to the central policy system, you only have to learn this policy system.

## Deploy Vault

Up to this point, we have been working with the "dev" server, which automatically authenticated us, setup in-memory storage, etc. Now that you know the basics of Vault, it is important to learn how to deploy Vault into a real environment.

Now we'll know how to configure Vault, start Vault, the seal/unseal process, and scaling Vault.

### Configuring Vault

Vault is configured using HCL files. The configuration file for Vault is relatively simple:

```pwsh
storage "consul" {
  address = "127.0.0.1:8500"
  path    = "vault/"
}

listener "tcp" {
 address     = "127.0.0.1:8200"
 tls_disable = 1
}
```

Within the configuration file, there are two primary configurations:

- ```storage``` - This is the physical backend that Vault uses for storage. Up to this point the dev server has used "inmem" (in memory), but the example above uses [Consul](https://www.consul.io/), a much more production-ready backend.

- ```listener``` - One or more listeners determine how Vault listens for API requests. The example above listens on localhost port 8200 without TLS. In your environment set ```VAULT_ADDR=http://127.0.0.1:8200``` so the Vault client will connect without TLS.

For now, copy and paste the configuration above to a file called ```config.hcl```. It will configure Vault to expect an instance of Consul running locally.

Starting a local Consul instance takes only a few minutes. Just follow the [Consul Getting Started Guide](https://learn.hashicorp.com/consul/getting-started/install.html) up to the point where you have installed Consul and started it with this command:

```pwsh
consul agent -dev
```

### Starting the Server

With the configuration in place, starting the server is simple, as shown below. Modify the ```-config``` flag to point to the proper path where you saved the configuration above.

```pwsh
vault server -config=config.hcl

==> Vault server configuration:

             Api Address: http://127.0.0.1:8200
                     Cgo: disabled
         Cluster Address: https://127.0.0.1:8201
              Listener 1: tcp (addr: "127.0.0.1:8200", cluster address: "127.0.0.1:8201", max_request_duration: "1m30s", max_request_size: "33554432", tls: "disabled")
               Log Level: info
                   Mlock: supported: false, enabled: false
           Recovery Mode: false
                 Storage: consul (HA available)
                 Version: Vault v1.3.2

==> Vault server started! Log data will stream in below:

```

> NOTE: If you get a warning message about mlock not being supported, that is okay. However, for maximum security you should run Vault on a system that supports mlock.

Vault outputs some information about its configuration, and then blocks. This process should be run using a resource manager such as systemd or upstart.

You'll notice that you can't execute any commands. We don't have any auth information! When you first setup a Vault server, you have to start by initializing it.

On Linux, Vault may fail to start with the following error:

```pwsh
vault server -config=config.hcl

Error initializing core: Failed to lock memory: cannot allocate memory

This usually means that the mlock syscall is not available.
Vault uses mlock to prevent memory from being swapped to
disk. This requires root privileges as well as a machine
that supports mlock. Please enable mlock on your system or
disable Vault from using it. To disable Vault from using it,
set the `disable_mlock` configuration option in your configuration
file.
```

For guidance on dealing with this issue, see the discussion of ```disable_mlock``` in [Server Configuration](https://www.vaultproject.io/docs/configuration).

### Initializing the Vault

Initialization is the process configuring the Vault. This only happens once when the server is started against a new backend that has never been used with Vault before. When running in HA mode, this happens once per cluster, not per server.

During initialization, the encryption keys are generated, unseal keys are created, and the initial root token is setup. To initialize Vault use ```vault operator init```. This is an unauthenticated request, but it only works on brand new Vaults with no data:

```pwsh
vault operator init

Unseal Key 1: 4jYbl2CBIv6SpkKj6Hos9iD32k5RfGkLzlosrrq/JgOm
Unseal Key 2: B05G1DRtfYckFV5BbdBvXq0wkK5HFqB9g2jcDmNfTQiS
Unseal Key 3: Arig0N9rN9ezkTRo7qTB7gsIZDaonOcc53EHo83F5chA
Unseal Key 4: 0cZE0C/gEk3YHaKjIWxhyyfs8REhqkRW/CSXTnmTilv+
Unseal Key 5: fYhZOseRgzxmJCmIqUdxEm9C3jB5Q27AowER9w4FC2Ck

Initial Root Token: s.KkNJYWF5g0pomcCLEmDdOVCW

Vault initialized with 5 key shares and a key threshold of 3. Please securely
distribute the key shares printed above. When the Vault is re-sealed,
restarted, or stopped, you must supply at least 3 of these keys to unseal it
before it can start servicing requests.

Vault does not store the generated master key. Without at least 3 key to
reconstruct the master key, Vault will remain permanently sealed!

It is possible to generate new unseal keys, provided you have a quorum of
existing unseal keys shares. See "vault operator rekey" for more information.
```

Initialization outputs two incredibly important pieces of information: the _unseal keys_ and the _initial root token_. This is the only time ever that all of this data is known by Vault, and also the only time that the unseal keys should ever be so close together.

For the purpose of this getting started guide, save all of these keys somewhere, and continue. In a real deployment scenario, you would never save these keys together. Instead, you would likely use Vault's PGP and Keybase.io support to encrypt each of these keys with the users' PGP keys. This prevents one single person from having all the unseal keys. Please see the documentation on [using PGP, GPG, and Keybase](https://www.vaultproject.io/docs/concepts/pgp-gpg-keybase.html) for more information.

### Seal/Unseal

Every initialized Vault server starts in the _sealed_ state. From the configuration, Vault can access the physical storage, but it can't read any of it because it doesn't know how to decrypt it. The process of teaching Vault how to decrypt the data is known as _unsealing_ the Vault.

Unsealing has to happen every time Vault starts. It can be done via the API and via the command line. To unseal the Vault, you must have the _threshold_ number of unseal keys. In the output above, notice that the "key threshold" is 3. This means that to unseal the Vault, you need 3 of the 5 keys that were generated.

>Note: Vault does not store any of the unseal key shards. Vault uses an algorithm known as [Shamir's Secret Sharing](https://en.wikipedia.org/wiki/Shamir%27s_Secret_Sharing) to split the master key into shards. Only with the threshold number of keys can it be reconstructed and your data finally accessed.

```pwsh
vault operator unseal

Unseal Key (will be hidden):
Key                Value
---                -----
Seal Type          shamir
Initialized        true
Sealed             true
Total Shares       5
Threshold          3
Unseal Progress    1/3
Unseal Nonce       d3d06528-aafd-c63d-a93c-e63ddb34b2a9
Version            1.3.4
HA Enabled         true
```

After pasting in a valid key and confirming, you'll see that the Vault is still sealed, but progress is made. Vault knows it has 1 key out of 3. Due to the nature of the algorithm, Vault doesn't know if it has the correct key until the threshold is reached.

Also notice that the unseal process is stateful. You can go to another computer, use vault operator unseal, and as long as it's pointing to the same server, that other computer can continue the unseal process. This is incredibly important to the design of the unseal process: multiple people with multiple keys are required to unseal the Vault. The Vault can be unsealed from multiple computers and the keys should never be together. A single malicious operator does not have enough keys to be malicious.

Continue with ```vault operator unseal``` to complete unsealing the Vault. To unseal the vault you must use three different unseal keys, the same key repeated will not work.

```pwsh
vault operator unseal

Unseal Key (will be hidden):
# ...
```

As you use keys, as long as they are correct, you should soon see output like this:

```pwsh
Key                    Value
---                    -----
Seal Type              shamir
Initialized            true
Sealed                 false
Total Shares           5
Threshold              3
Version                1.3.4
Cluster Name           vault-cluster-df0d8ee9
Cluster ID             c91bc0f4-3500-8293-23f4-ab6e1ec317a3
HA Enabled             true
HA Cluster             n/a
HA Mode                standby
Active Node Address    <none>
```

When the value for ```Sealed``` changes to ```false```, the Vault is unsealed.

Feel free to play around with entering invalid keys, keys in different orders, etc. in order to understand the unseal process.

Finally, authenticate as the initial root token (it was included in the output with the unseal keys):

```pwsh
vault login s.KkNJYWF5g0pomcCLEmDdOVCW

Success! You are now authenticated. The token information displayed below
is already stored in the token helper. You do NOT need to run "vault login"
again. Future Vault requests will automatically use this token.

Key                  Value
---                  -----
token                s.KkNJYWF5g0pomcCLEmDdOVCW
token_accessor       9jZ4x92RbzLqwLPlb9rVAMY9
token_duration       ∞
token_renewable      false
token_policies       ["root"]
identity_policies    []
policies             ["root"]
```

As a root user, you can reseal the Vault with ```vault operator seal```. A single operator is allowed to do this. This lets a single operator lock down the Vault in an emergency without consulting other operators.

When the Vault is sealed again, it clears all of its state (including the encryption key) from memory. The Vault is secure and locked down from access.

You now know how to configure, initialize, and unseal/seal Vault. This is the basic knowledge necessary to deploy Vault into a real environment. Once the Vault is unsealed, you access it as you have throughout this getting started guide (which worked with an unsealed Vault).

## Using the HTTP APIs with Authentication

All of Vault's capabilities are accessible via the HTTP API in addition to the CLI. In fact, most calls from the CLI actually invoke the HTTP API. In some cases, Vault features are not available via the CLI and can only be accessed via the HTTP API.

Once you have started the Vault server, you can use Client URL (cURL) or any other http client to make API calls. For example, if you started the Vault server in dev mode, you could validate the initialization status like this:

```pwsh
curl http://127.0.0.1:8200/v1/sys/init
```

This will return a JSON response:

```json
{
  "initialized": true
}
```

### Accessing Secrets via the REST APIs

Machines that need access to information stored in Vault will most likely access Vault via its REST API. For example, if a machine were using [AppRole](https://www.vaultproject.io/docs/auth/approle.html) for authentication, the application would first authenticate to Vault which would return a Vault API token. The application would use that token for future communication with Vault.

For the purpose of this guide, we will use the following configuration which disables TLS and uses a file-based backend. TLS is disabled here only for example purposes; it should never be disabled in production.

```pwsh
backend "file" {
  path = "vault"
}

listener "tcp" {
  tls_disable = 1
}

```

Save this file on disk as ```config.hcl```. Stop the Vault server instance that you previously started and then start a new instance using the newly created configuration.

At this point, we can use Vault's API for all our interactions. For example, we can initialize Vault like this.

> NOTE: This example uses jq to process the JSON output for readability.

```bash
curl \
    --request POST \
    --data '{"secret_shares": 1, "secret_threshold": 1}' \
    http://127.0.0.1:8200/v1/sys/init | jq

```

The response should be JSON and looks something like this:

```JSON
{
  "keys": [
    "ff27b63de46b77faabba1f4fa6ef44c948e4d6f2ea21f960d6aab0eb0f4e1391"
  ],
  "keys_base64": [
    "/ye2PeRrd/qruh9Ppu9EyUjk1vLqIflg1qqw6w9OE5E="
  ],
  "root_token": "s.Ga5jyNq6kNfRMVQk2LY1j9iu"
}
```

This response contains our initial root token. It also includes the unseal key. You can use the unseal key to unseal the Vault and use the root token perform other requests in Vault that require authentication.

To make this guide easy to copy-and-paste, we will be using the environment variable ```$VAULT_TOKEN``` to store the root token. You can export this Vault token in your current shell like this:

```bash
export VAULT_TOKEN="s.Ga5jyNq6kNfRMVQk2LY1j9iu"
```

Using the unseal key (not the root token) from above, you can unseal the Vault via the HTTP API:

```bash
curl \
    --request POST \
    --data '{"key": "/ye2PeRrd/qruh9Ppu9EyUjk1vLqIflg1qqw6w9OE5E="}' \
    http://127.0.0.1:8200/v1/sys/unseal | jq
```

Note that you should replace /ye2PeRrd/qru... with the generated key from your output. This will return a JSON response:

```JSON
{
  "type": "shamir",
  "initialized": true,
  "sealed": false,
  "t": 1,
  "n": 1,
  "progress": 0,
  "nonce": "",
  "version": "1.3.2",
  "migration": false,
  "cluster_name": "vault-cluster-a90e2cd2",
  "cluster_id": "0bc4b0fa-f876-8069-8d45-e0daae74e90e",
  "recovery_seal": false,
  "storage_type": "file"
}
```

Now any of the available auth methods can be enabled and configured. For the purposes of this guide lets enable [AppRole](https://www.vaultproject.io/docs/auth/approle.html) authentication.

The [Authentication](https://learn.hashicorp.com/vault/getting-started/authentication#auth-methods) guide showed how to enable the GitHub auth method using Vault CLI.

```pwsh
vault auth enable <auth_method_type>
```

To see the cURL equivalent of the CLI command to enable AppRole auth method, use the ```-output-curl-string``` flag.

```pwsh
vault auth enable -output-curl-string approle
```

Enable the AppRole auth method by invoking the Vault API.

```bash
curl \
    --header "X-Vault-Token: $VAULT_TOKEN" \
    --request POST \
    --data '{"type": "approle"}' \
    http://127.0.0.1:8200/v1/sys/auth/approle
```

Notice that the request to enable the AppRole endpoint needed an authentication token. In this case we are passing the root token generated when we started the Vault server. We could also generate tokens using any other authentication mechanisms, but we will use the root token for simplicity.

Now create an AppRole with desired set of [ACL policies](https://www.vaultproject.io/docs/concepts/policies.html).

The [Policies](https://learn.hashicorp.com/vault/getting-started/policies) guide used CLI to create my-policy. In this guide, use the ```/sys/policies/acl``` endpoint to create the same policy via Vault API.

```bash
curl \
    --header "X-Vault-Token: $VAULT_TOKEN" \
    --request PUT \
    --data '{"policy":"# Dev servers have version 2 of KV secrets engine mounted by default, so will\n# need these paths to grant permissions:\npath \"secret/data/*\" {\n  capabilities = [\"create\", \"update\"]\n}\n\npath \"secret/data/foo\" {\n  capabilities = [\"read\"]\n}\n"}' \
    http://127.0.0.1:8200/v1/sys/policies/acl/my-policy

```

Since ```my-policy``` expects ```secret/data``` path to exist, enable KV v2 secrets engine at ```secret/``` using API.

```bash
curl \
    --header "X-Vault-Token: $VAULT_TOKEN" \
    --request POST \
    --data '{ "type":"kv-v2" }' \
    http://127.0.0.1:8200/v1/sys/mounts/secret

```

The following command specifies that the tokens issued under the AppRole ```my-role``` should be associated with ```my-policy```.

```bash
curl \
    --header "X-Vault-Token: $VAULT_TOKEN" \
    --request POST \
    --data '{"policies": ["my-policy"]}' \
    http://127.0.0.1:8200/v1/auth/approle/role/my-role
```

The AppRole auth method expects a RoleID and a SecretID as its input. The RoleID is similar to a username and the SecretID can be thought as the RoleID's password.

The following command fetches the RoleID of the role named ```my-role```.

```bash
curl \
    --header "X-Vault-Token: $VAULT_TOKEN" \
     http://127.0.0.1:8200/v1/auth/approle/role/my-role/role-id | jq -r ".data"
```

The response will include the role_id:

```JSON
{
  "role_id": "3c301960-8a02-d776-f025-c3443d513a18"
}
```

This command creates a new SecretID under the ```my-role```.

```bash
curl \
    --header "X-Vault-Token: $VAULT_TOKEN" \
    --request POST \
    http://127.0.0.1:8200/v1/auth/approle/role/my-role/secret-id | jq -r ".data"

```

The response will include the ```secret_id```:

```JSON
{
  "secret_id": "22d1e0d6-a70b-f91f-f918-a0ee8902666b",
  "secret_id_accessor": "726ab786-70d0-8cc4-e775-c0a75070e5e5"
}

```

These two credentials can be supplied to the login endpoint to fetch a new Vault token.

```bash
curl --request POST \
       --data '{"role_id": "c3ec4eab-5477-c669-fca8-6a71fdf38c23", "secret_id": "fc2710e5-9536-3f4f-666d-fd5d8379b2b9"}' \
       http://127.0.0.1:8200/v1/auth/approle/login | jq -r ".auth"
```

The response will be JSON, under the key auth:

```JSON
{
  "client_token": "s.p5NB4dTlsPiUU94RA5IfbzXv",
  "accessor": "EQTlZwOD4yIFYWIg5YY6Xr29",
  "policies": [
    "default",
    "my-policy"
  ],
  "token_policies": [
    "default",
    "my-policy"
  ],
  "metadata": {
    "role_name": "my-role"
  },
  "lease_duration": 2764800,
  "renewable": true,
  "entity_id": "4526701d-b8fd-3c39-da93-9e17506ec894",
  "token_type": "service",
  "orphan": true
}
```

The returned client token (```s.p5NB4dTlsPiUU94RA5IfbzXv```) can be used to authenticate with Vault. 

This token will be authorized with specific capabilities on all the resources encompassed by the ```default``` and ```my-policy``` policies. (As it was mentioned in the Policies guide, the default policy is attached to all tokens by default. )

The newly acquired token can be exported as the ```VAULT_TOKEN``` environment variable value and used to authenticate subsequent Vault requests.

```bash
export VAULT_TOKEN="s.p5NB4dTlsPiUU94RA5IfbzXv"
```

Create a version 1 of secret named ```creds``` with a key ```password``` and its value set to ```my-long-password```.

```bash
curl \
    --header "X-Vault-Token: $VAULT_TOKEN" \
    --request POST \
    --data '{ "data": {"password": "my-long-password"} }' \
    http://127.0.0.1:8200/v1/secret/data/creds | jq -r ".data"

```

```JSON
{
  "created_time": "2020-02-05T16:51:34.0887877Z",
  "deletion_time": "",
  "destroyed": false,
  "version": 1
}
```

You can stop the server and unset the VAULT_TOKEN environment variable.

```bash
unset VAULT_TOKEN
```

You can see the documentation on the [HTTP APIs](https://www.vaultproject.io/api-docs) for more details on other available endpoints.

## Web UI

Vault features a user interface (web interface) for interacting with Vault. Easily create, read, update, and delete secrets, authenticate, unseal, and more with the Vault UI.

### Dev servers

When you start the Vault server in dev mode, Vault UI is automatically enabled and ready to use.

Open a web browser and enter <http://127.0.0.1:8200/ui> to launch the UI.

Enter the initial root token to sign in.

### Non-Dev servers

The Vault UI is not activated by default. To activate the UI, set the ui configuration option in the Vault server configuration.

```bash
ui = true

listener "tcp" {
  # ...
}

storage "consul" {
  # ...
}
```

The UI runs on the same port as the Vault listener. As such, you must configure at least one ```listener``` stanza in order to access the UI.

```bash
ui = true

listener "tcp" {
  address = "10.0.1.35:8200"

  # If bound to localhost, the Vault UI is only
  # accessible from the local machine!
  # address = "127.0.0.1:8200"
}
# ...

```

In this case, the UI is accessible the following URL from any machine on the subnet (provided no network firewalls are in place): <https://10.0.1.35:8200/ui>

It is also accessible at any DNS entry that resolves to that IP address, such as the Consul service address (if using Consul): <https://vault.service.consul:8200/ui>

### Web UI Wizard

Vault UI has a built-in guide to navigate you through the common steps to operate various Vault features.


## Next Steps 

Due to the importance of securing secrets, we recommend reading the following as next steps.

- [Documentation](https://www.vaultproject.io/docs) - The documentation is an in-depth reference guide to all the features of Vault.