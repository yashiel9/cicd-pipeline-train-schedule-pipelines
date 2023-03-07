pipeline {
  agent any

  environment {
    VAULT_ADDR = 'http://host.docker.internal:8200'
    // VAULT_APPROLE_ROLE_ID = credentials('vault-approle-role-id')
  }

  stages {
    stage('Authenticate to Vault') {
      steps {
        // withVault(configuration: [timeout: 60, 
        // vaultCredentialId: 'vault-jenkins-role-dev', 
        // vaultUrl: 'http://host.docker.internal:8200']) {
        //   script {
        //   // Define the API request data
        //   // Make the API request with curl
        //             // --header 'X-Vault-Token: $VAULT_TOKEN' \
        //   //  sh "curl \
        //   //   --request GET \
        //   //   --silent \
        //   //   --output ~/roleinfo.json \
        //   //   $VAULT_ADDR/v1/ldap/static-cred/learn"
        //           sh 'echo TOKEN=$VAULT_TOKEN'
        //           sh 'echo ADDR=$VAULT_ADDR'
        // }
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
    // stage('Build') {
    //   steps {
    //     echo 'Running build automation'
    //     script {
    //       // Define the API request data
    //       // Make the API request with curl
    //                 // --header 'X-Vault-Token: $VAULT_TOKEN' \
    //        sh "curl \
    //         --request POST \
    //         --silent \
    //         --data @data/learn-vault-ldap-role.json \
    //         --output response.txt \
    //         $VAULT_ADDR/v1/ldap/static-role/learnFromJenkins"

    //       def response = readFile('response.txt')
    //       if (response.contains('error')) {
    //         error 'API call failed '
    //       } else {
    //         echo 'API call successful'
    //       }
          
    //       //archiveArtifacts artifacts: 'dist/roleDetails.zip'
    //     }
    //   }
    // }
  }
}
