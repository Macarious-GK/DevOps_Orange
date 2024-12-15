vault auth enable approle
vault write auth/approle/role/jenkins-role token_num_uses=0 secret_id_num_uses=0 policies="jenkins"
vault read auth/approle/role/jenkins-role/role-id
vault write -f auth/approle/role/jenkins-role/secret-id
vault secrets enable -path=secrets kv
vault write secrets/creds/vagrant username=siva password=siva
vault write secrets/creds/DB_Pass secret=123456789
vault write secrets/creds/DB_User secret=user1


vault policy write jenkins jenkins-policy.hcl