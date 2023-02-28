pipeline {
 agent any
  stages {
    stage('Build') {
      steps {
        echo 'Running build automation'
        script {
          // Define the API request data
          // Make the API request with curl
           sh "curl \
            --header 'X-Vault-Token: $api_token' \
            --request POST \
            --silent \
            --data @data/learn-vault-ldap-role.json \
            $VAULT_ADDR/v1/ldap/static-role/learnFromJenkins"

          
          //archiveArtifacts artifacts: 'dist/roleDetails.zip'
        }
      }
    }
  }
}
