pipeline {
    agent any
    stages {
        stage('Descargar Código') {
            steps {
                echo 'Clonando el repositorio desde GitHub...'
                git branch: 'desarrollo', url: 'https://github.com/DiegoGilSanz/proyecto-devsecops.git'
            }
        }
        stage('Construir Imagen Docker (Build)') {
            steps {
                echo 'Construyendo el contenedor seguro...'
                sh 'docker build -t mi-app-segura:latest .'
            }
        }
        stage('Análisis de Seguridad (Trivy)') {
            steps {
                echo 'Buscando vulnerabilidades CRÍTICAS...' [cite: 1]
                sh 'docker run --rm -v /var/run/docker.sock:/var/run/docker.sock ghcr.io/aquasecurity/trivy:latest image --exit-code 1 --severity CRITICAL mi-app-segura:latest' [cite: 1]
            }
        }
        stage('Despliegue en Producción (CD)') {
            steps {
                echo '¡Imagen limpia! Desplegando en el servidor...' [cite: 1]
                sh 'docker stop app-produccion || true' [cite: 1]
                sh 'docker rm app-produccion || true' [cite: 1]
                sh 'docker run -d --name app-produccion mi-app-segura:latest' [cite: 1]
            }
        }
    }
}