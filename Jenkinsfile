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
                echo 'Ejecutando pruebas unitarias...'
                // set CI=true evita que los tests se queden esperando interacción del usuario
                bat 'set CI=true&&npm.cmd test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Iniciando despliegue local en la VM...'
                script {
                    /* 
                       1. Intentamos detener cualquier proceso de Node previo en el puerto 3000.
                       2. 'taskkill' forzará el cierre de instancias antiguas de la app.
                       3. Usamos '|| ver > nul' para que si no hay procesos abiertos, el pipeline no falle.
                    */
                    bat "taskkill /F /IM node.exe /T || ver > nul"

                    /* 
                       4. Lanzamos la aplicación.
                       5. 'start /B' es CRUCIAL: abre el proceso en segundo plano (background).
                       6. Sin '/B', Jenkins se quedaría "colgado" esperando a que la app se cierre.
                    */
                    bat "start /B npm.cmd start"
                    
                    echo 'PROCESO FINALIZADO: La aplicación está corriendo en http://localhost:3000'
                }
            }
        }
    }
