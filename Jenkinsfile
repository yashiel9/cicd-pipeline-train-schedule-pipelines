pipeline {
  agent any

  environment {
    VAULT_ADDR = 'http://host.docker.internal:8200'
  }

  stages {
    stage('Authenticate to Vault') {
      steps {
        withCredentials([[$class: 'VaultTokenCredentialBinding', 
        addrVariable: 'VAULT_ADDR', 
        credentialsId: 'vault-jenkins-role-dev', 
        tokenVariable: 'VAULT_TOKEN', 
        vaultAddr: 'http://host.docker.internal:8200']]) {
          sh "curl \
          --header 'X-Vault-Token: $VAULT_TOKEN' \
          --request POST \
          --silent \
          --data @data/learn-vault-ldap-role.json \
          $VAULT_ADDR/v1/ldap/static-role/learn2"

          // step('Read response') {
          //   def response = readFile('response.txt')
          //   if (response.contains('error')) {
          //     error 'API call failed '
          //   } else {
          //     echo 'API call successful'
          //   }
          // }
          
    //       sh 'curl \
    // --header "X-Vault-Token: $VAULT_TOKEN" \
    // --request GET \
    // $VAULT_ADDR/v1/ldap/static-role/learn'
          
        }
      }
    }
  }
}
