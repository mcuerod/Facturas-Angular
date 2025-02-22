pipeline {
    agent any
    environment {
        AZURE_WEBAPP_ANGULAR = 'miapp-angular'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/mcuerod/Facturas-Angular.git'
            }
        }
        stage('Install Dependencies') {
            steps {
                sh 'npm install' // Instala las dependencias de Angular
            }
        }
        stage('Build Angular') {
            steps {
                sh 'ng build --configuration=production' // Construye la app en modo producción
            }
        }
        stage('Deploy to Azure') {
            steps {
                sh "az webapp deploy --resource-group mi-recurso --name ${AZURE_WEBAPP_ANGULAR} --src-path dist/fa-prb"
            }
        }
    }
}
