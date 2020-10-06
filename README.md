# Kyma Token as GCP Auth-Provider

This script helps cluster users to auto-update kyma token to their configuration/cache.

Only works with gitlab authentication using username/password. TODO: Login with email/password of internal dex.

This script uses kubectl command to add kyma cluster kubeconfig to your kubectl configuration file

If no context is specified, use kubectl config current-context.

Note: This script puts itself in kubectl, if you move it after configuration, run it with -k to save in kubectl config the new location

## Installation
Put this script in the bin path you prefer:
    /usr/local/bin

Install the requirements with (pip3): pip3 install -r requirements.txt

## First use: (if wanna use current-context from kubectl omit context argument)
    kyma-as-gcp-provider -c context -u gitlab_username

1. Will ask for password
2. Adds context to kubectl if not exists
3. If you don't have access to kyma cluster brings an error
4. Password is saved to your keyring

## Requeriments (autogenerate if not exists):
Packages with apt/yum:
    python3
    python3-pip
    python3-openssl
    python3-ldap
Requirements file requirements.txt

Config file on: ~/.config/kyma-as-gcp-provider/config


## Force save kyma kubeconfig to your kubectl config file
kyma-as-gcp-provider -k

## Force password change (ask for it!):
kyma-as-gcp-provider -p

## To save configuration changes use --save:
kyma-as-gcp-provider -u newuser -p --save