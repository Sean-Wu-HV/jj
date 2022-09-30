pipeline {
    agent any 
    environment {
        ABC = "hi"
    }
    properties([
      parameters([
        booleanParam(
          defaultValue: false,
          description: 'isFoo should be false',
          name: 'isFoo'
        ),
        booleanParam(
          defaultValue: true,
          description: 'isBar should be true',
          name: 'isBar'
        ),
          string(name: 'VERSION_TO_LIST', defaultValue: "9.1"),
          string(name: 'ARTIFACTORY_CREDENTIALS', defaultValue: "nabc"),
      ])
    ])
    stages {
        stage ('Clean and build'){
            steps{
                sh "pwd"
                sh "whoami"
                sh "ls -la"
                sh "uname"
                sh "echo 'heehee'"
                sh "echo isFoo $isFoo"
                sh "echo isBar $isBar"
                sh "echo isBar $VERSION_TO_LIST"
                sh "echo isBar $ARTIFACTORY_CREDENTIALS"
            }
        }
        stage ('SonarQube analysis'){
            steps{
                script{
                    script{
                       def scannerHome = tool 'SonarQube Scanner';
                       withSonarQubeEnv('Sonarqube') {
                           sh "${tool("SonarQube Scanner")}/bin/sonar-scanner -Dsonar.projectKey=hvs-cli -Dsonar.projectName=hvs-cli"
                       }
                    }
                }
            }
        }
    }
    post
    {
        success {
            echo "done success"
        }
        failure {
            echo "done fail"
        }
        always{
            echo "done always"
        }
    }
}
