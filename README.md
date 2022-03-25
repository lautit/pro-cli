# pro-cli
Simple CLI, made with Rust, to communicate with Prometeo Open Banking API.

# Where to start

## Setup

- Generate your own API key by creating your account in [Prometeo Dashboard](https://prometeoapi.com), them allow the CLI to access it by setting `PRO_CLI_API_KEY=myReallyCoolAPIKey`
- Select your desired scope (`prduction`, `testing` or `sandbox`) by setting `PRO_CLI_SCOPE=[production|testing|sandbox]`

You can also save all these settings to `~/.proclirc`. 

# How this works

## Authentication

### [Login](https://docs.prometeoapi.com/reference/login) - `login`
Start a session with a financial institution

```shell
pro-cli login "{provider}" "[{type}]" --username {username} --password {password}`
```

Needs a valid Promoteo API key. Can fail if username or password are invalid, user is locked, or user is already logged or has reached available session limit.

It will generate a session key, which will be saved internally for any subsequent commands.

#### Options
- `-u, --username`: username for ebanking or app
- `-p, --password`: password for username
- `{provider}`: name of the ebanking or app provider, should be one of the `pro-cli p` results 
- `{type}` _(optional)_: depending on your provider, specifies account type

### [Logout](https://docs.prometeoapi.com/reference/logout) - `logout`
Close current session, invalidating session key

```shell
pro-cli logout
```

## Transactional

### [Accounts](https://docs.prometeoapi.com/reference/getaccounts) - `accounts|a`
List all the accounts related to the user

```shell
pro-cli accounts
```

### [Credit cards](https://docs.prometeoapi.com/reference/getcreditcards) - `credit-cards|c`
List all the credit cards associated with the user

```shell
pro-cli credit-cards
```

## Meta

### [Providers](https://docs.prometeoapi.com/reference/getproviders) - `providers|p`
List all the data providers available in the Prometeo API

```shell
pro-cli providers
```

