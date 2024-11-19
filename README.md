## Module certificate

### Structure
- **main.tf**
- **variables.tf**
- **outputs.tf**

### Usage module

Certificate
```hcl
module "certificates" {
  source = "git@github.com:Sparg/tf-module-az-cert.git?ref=<release-tag>"

  algorithm = var.algorithm
  rsa_bits  = var.rsa_bits
}
```

### Outputs module

Certificate
- `public_ip`
- `private_key`

### Note:

Depending on the environment used, you may encounter problems with the extraction and use of the private key, due to permissions issues.

If you encounter this problem use the following command inside “Git Bash”:

```bash
$ terraform output public_ip_address
$ terraform output tls_private_key
$ terraform output -raw tls_private_key > file
$ chmod 600 file
$ ssh user@public_ip -i file
```

Shortcut to open “Git Bash” terminal:
```bash
$ "C:\Program Files\Git\bin\bash.exe" --login -i
```