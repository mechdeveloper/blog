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

### Writing a Secret

vault kv command

```pwsh
vault kv put secret/hello foo=world
```

This writes the pair foo=world to the path secret/hello. 

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

```pwsh
vault secrets disable kv/
```

Note that this command takes a PATH to the secrets engine as an argument, not the TYPE of the secrets engine.

Any requests to route data to the original path would result in an error, but another secrets engine could now be enabled at that path.

## Next Steps 

Due to the importance of securing secrets, it's recommend reading the following as next steps.

- [Documentation](https://www.vaultproject.io/docs) - The documentation is an in-depth reference guide to all the features of Vault.