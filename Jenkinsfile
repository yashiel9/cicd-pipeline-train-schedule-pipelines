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
            --output response.txt \
            $VAULT_ADDR/v1/ldap/static-role/learnFromJenkins"

          def response = readFile('response.txt')
          if (response.contains('error')) {
            error 'API call failed '
          } else {
            echo 'API call successful'
          }
          
          //archiveArtifacts artifacts: 'dist/roleDetails.zip'
        }
      }
    }
  }
}
