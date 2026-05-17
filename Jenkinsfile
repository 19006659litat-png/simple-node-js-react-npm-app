// Reconozco que este código por simple que es, fue generado con IA Gemini, ya que este repositorio está siendo útil para el aprendizaje. 

pipeline {
    agent any
    stages {
        stage('Build') { 
            steps {
                bat 'npm.cmd install' 
                bat 'npm.cmd run build' 
            }
        }
        Stage('Test') {
            steps {
                bat 'npm.cmd test'
            }
        }
    }
}
