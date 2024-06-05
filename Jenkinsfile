pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                script {
                    sh '''
                        /usr/local/bin/node /usr/local/bin/newman run /path/to/API_Tests.postman_collection.json -e /path/to/API_Environment.postman_environment.json -d /path/to/data.json --suppress-exit-code -r html --reporter-html-export /path/to/report.html
                    '''
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
        stage('Archive Report') {
            steps {
                sh 'ls /path/to/report.html' // Verifica que el archivo de reporte exista
                archiveArtifacts artifacts: '/path/to/report.html', fingerprint: true
            }
        }
    }
}