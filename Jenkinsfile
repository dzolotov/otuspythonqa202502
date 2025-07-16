pipeline {
    agent {
        docker {
             image 'python:3.11'
        }
    }
    stages {
        stage('Tests') {
            steps {
                git branch: 'main', url: 'https://github.com/dzolotov/otuspythonqa202502'
                sh 'python3 -m pip install pytest'
                sh 'python3 -m pytest . --junit-xml=report.xml'
                junit keepProperties: true, keepTestNames: true, stdioRetention: 'ALL', testResults: 'report.xml'
            }
        }
    }
}
