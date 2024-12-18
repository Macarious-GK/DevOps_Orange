# Vault  
A small and simple guide for setting up HashiCorp Vault in **Development** and **Production** modes.

![Vault Logo](/Figures/vault_logo.png)

---

## Table of Contents  
1. [Setup Vault in Dev Mode](#setup-vault-in-dev-mode)  
2. [Setup Vault for Production](#setup-vault-for-production)  
3. [Vault Authentication and Secrets Configuration](#vault-authentication-and-secrets-configuration)  
4. [Vault Policies](#vault-policies)  

---

## Setup Vault in Dev Mode  

To start Vault in **Dev mode** with TLS enabled:  

1. **Start Vault in Dev mode**  
   ```bash
   vault server -dev -dev-root-token-id=root -dev-tls -dev-listen-address="0.0.0.0:8200"
    ```
2. **Start Vault in Dev mode**  
   ```bash
    export VAULT_ADDR='https://127.0.0.1:8200'
    ```
3. **Check Vault status**  
   ```bash
    vault status
    ```
4. **Login to Vault**  
   ```bash
    vault login root
    ```
5. **Stop Vault and unset environment variables**  
   ```bash
    pkill vault
    unset VAULT_ADDR VAULT_CACERT    
    ```

## Setup Vault for Production  

To configure Vault for a **Production environment**:  

1. **Start Vault using a configuration file**  
   ```bash
    vault server -config=/home/vagrant/vault_server/vault-server.hcl

    ```
2. **Initialize Vault**  
   ```bash
    vault operator init -key-shares=1 -key-threshold=1

    ```
3. **Seal and Unseal Vault**  
   ```bash
    vault operator seal
    vault operator unseal <Unseal-Key>
    ```



## Vault Authentication and Secrets Configuration  
- This is a show case on Mysql_Secrets
- To start Vault in **Dev mode** or **Production mode**:  

1. **Enable AppRole Authentication**  
   ```bash
   vault auth enable approle

    ```
2. **Create a Role for Jenkins**  
   ```bash
    vault write auth/approle/role/jenkins-role token_num_uses=0 secret_id_num_uses=0 policies="jenkins"
    ```
3. **Retrieve Role ID and Secret ID**  
   ```bash
    vault read auth/approle/role/jenkins-role/role-id
    vault write -f auth/approle/role/jenkins-role/secret-id

    ```
4. **Enable KV Secrets Engine**  
    ```bash
    vault secrets enable -path=secrets kv

    ```

5. **Write Secrets**  
   ```bash
   vault write secrets/creds/vagrant username=vagrant password=vagrant
   vault write secrets/creds/DB_Pass secret=123456789
   vault write secrets/creds/DB_User secret=user1
  
    ```

## Vault Policies

- Vault policies define access rules for secrets and operations. Here's an example policy for **Jenkins**:
1. **Create a Policy File (jenkins-policy.hcl):**



```hcl
path "secrets/*" {
    capabilities = ["create", "read", "update", "delete", "list"]
}

```
2. **Apply the Policy:**
```bash

vault policy write jenkins jenkins-policy.hcl
```

![Vault_IN_Work](/Figures/vault_working.png)
