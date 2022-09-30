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
