pipeline {
    agent { docker 'ubuntu' }
    environment {
        ABC = "hi"
    }
    stages {
        stage ('Clean and build'){
            steps{
                sh "dotnet clean build"
                sh "heehee"
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
