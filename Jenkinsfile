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
                    sh '/usr/local/bin/node /usr/local/bin/newman run /postman_jenkins_api_tests/tests/API_Tests.postman_collection.json -e /postman_jenkins_api_tests/environment/API_Environment.postman_environment.json -d /postman_jenkins_api_tests/tests/data.json --suppress-exit-code -r html --reporter-html-export /usr/local/bin/reporte/report.html'
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
                archiveArtifacts artifacts: '/usr/local/bin/reporte/report.html', fingerprint: true
            }
        }
    }
}