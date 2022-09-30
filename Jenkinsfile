pipeline {
    agent any 
    environment {
        ABC = "hi"
    }
    stages {
        stage ('Clean and build'){
            steps{
                sh "pwd"
                sh "whoami"
                sh "ls -la"
                sh "uname"
                sh "echo 'heehee'"
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
