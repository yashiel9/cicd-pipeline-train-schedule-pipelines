pipeline {
  agent any

  environment {
    VAULT_ADDR = 'http://host.docker.internal:8200'
    ROLE_NAME = 'learn2'
  }

  parameters {
    string(name: 'ROLE_NAMES', defaultValue: 'role1,role2,role3', description: 'Comma-separated list of role names to create in Vault')
  }

  stages {
    stage('Authenticate to Vault') {
      steps {
        withCredentials([[$class: 'VaultTokenCredentialBinding', 
        addrVariable: 'VAULT_ADDR', 
        credentialsId: 'vault-jenkins-role-dev', 
        tokenVariable: 'VAULT_TOKEN', 
        vaultAddr: 'http://host.docker.internal:8200']]) {
          sh "export TOKEN = $VAULT_TOKEN"
          // sh "curl \
          // --header 'X-Vault-Token: $VAULT_TOKEN' \
          // --request POST \
          // --silent \
          // --data @data/learn-vault-ldap-role.json \
          // $VAULT_ADDR/v1/ldap/static-role/$ROLE_NAME"

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

    stage('Iterating over Array of roles') {
      steps {
        script {
            sh "hello"
        }
      }
    }
  }
}
