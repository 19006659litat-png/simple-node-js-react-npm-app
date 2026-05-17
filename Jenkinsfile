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
        stage('Deploy') {
            steps {
                script {
                    // 1. Limpiamos
                    bat "taskkill /F /IM node.exe /T || ver > nul"
                    
                    // 2. Intentamos lanzar la app forzando el puerto 3000 y 
                    // enviando la salida a un archivo para ver si hay errores ocultos
                    bat "set PORT=3000&& start /B npm.cmd start > output.log 2>&1"
                    
                    // 3. Esperamos un poco para que Node logre estabilizarse
                    bat "timeout /t 10 /nobreak"
                }
        }
    }
    }

    post {
        success {
            echo '¡Pipeline ejecutado con éxito!'
        }
        failure {
            echo 'El Pipeline falló. Revisa el Console Output para más detalles.'
        }
    }
}
