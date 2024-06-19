pipeline {
    agent {
        docker { image 'node:16:lts' }
    }
    stages {
        stage('Test') {
            steps {
                sh 'node --version'
            }
        }
    }
}