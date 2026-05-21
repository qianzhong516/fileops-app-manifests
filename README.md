# FileOps App Manifests

## Using SOPS to encrypt secrets uploaded to Git

Set up env variables:

```bash
export SOPS_KMS_ARN="......"
export AWS_ACCESS_KEY_ID="......"
export AWS_SECRET_ACCESS_KEY="......"
```

Encrypt the Secret manifest:

```bash
sops --encrypt secret.yml > secret.enc.yml
```

SOPS will factor in rules from `.sops.yml`. After that, to edit secrets:

```bash
sops edit secret.enc.yml
```

SOPS rotate a key

Update the key in `.sops.yaml` and run:

```bash
sops updatekeys base/secret.enc.yml
sops -r -i base/secret.enc.yml
```
