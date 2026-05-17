pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                bat 'npm.cmd install' 
                bat 'npm.cmd run build' 
            }
        }
    }
}
