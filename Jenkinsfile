// Reconozco que este código por simple que es, fue generado con IA Gemini, ya que este repositorio está siendo usado para aprendizaje. 

pipeline {
    agent any

    stages {
        stage('Build') { 
            steps {
                echo 'Instalando dependencias y construyendo la aplicación...'
                bat 'npm.cmd install' 
                bat 'npm.cmd run build' 
            }
        }

        stage('Test') {
            steps {
                //echo 'Ejecutando pruebas unitarias...'
                // set CI=true evita que los tests se queden esperando interacción del usuario
                bat 'set CI=true&&npm.cmd test'
            }
        }
    }
