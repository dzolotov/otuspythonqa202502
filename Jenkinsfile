pipeline {
    agent any
    stages {
        stage('Tests') {
            steps {
                script {
                    docker.image('python:3.11').inside {
                        checkout scm
                        sh 'python3 -m pip install pytest'
                        sh 'python3 -m pytest . --junit-xml=report.xml'
                    }
                }
                junit keepProperties: true, keepTestNames: true, stdioRetention: 'ALL', testResults: 'report.xml'
            }
        }
    }
}
