# FileOps App Manifests

## Using SOPs to encrypt secrets uploaded to Git

Set up env variables:

```bash
export SOPS_KMS_ARN="......"
export AWS_ACCESS_KEY_ID="......"
export AWS_SECRET_ACCESS_KEY="......"
```

Encrypt the Secret manifest:

```bash
sops --encrypt secrets.yml > secrets.enc.yml
```

SOPs will factor in rules from `.sops.yml`. After that, to edit secrets:

```bash
sops edit secrets.enc.yml
```
