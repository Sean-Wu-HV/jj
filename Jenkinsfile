
pipeline {
    agent any 
    environment {
        ABC = "hi"
    }
    parameters{
        booleanParam(
          defaultValue: false,
          description: 'isFoo should be false',
          name: 'isFoo'
        )
        booleanParam(
          defaultValue: true,
          description: 'isBar should be true',
          name: 'isBar'
        )
        string(name: 'VERSION_TO_LIST', defaultValue: "9.1")
        string(name: 'ARTIFACTORY_CREDENTIALS', defaultValue: "nabc")
    }
    stages {
        stage ('Clean and build'){
            steps{
                sh "pwd"
                sh "whoami"
                sh "ls -la"
                sh "uname"
                sh "echo 'heehee'"
                sh "echo isFoo ${params.isFoo}"
                sh "echo isBar ${params.isBar}"
                sh "echo isBar ${params.VERSION_TO_LIST}"
                sh "echo isBar ${params.ARTIFACTORY_CREDENTIALS}"
                sh "echo ${env.ABC}"
            }
        }
        stage ('SonarQube analysis'){
            steps{
                script{
                    script{
                       def scannerHome = tool 'SonarQube Scanner';
                       withSonarQubeEnv('sonarqube') {
                           sh "ls -la"
                           sh "echo ${scannerHome}"
                           sh "${scannerHome}/bin/sonar-scanner"
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
