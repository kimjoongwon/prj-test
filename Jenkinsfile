pipeline {
    agent any

    environment {
        // 환경 변수 설정
        NODE_VERSION = '20'
    }

    stages {
        stage('Prepare') {
            steps {
                // Node.js 버전 설정
                sh 'nvm install $NODE_VERSION'
                sh 'nvm use $NODE_VERSION'
                // 의존성 설치
                sh 'npm install'
            }
        }

        stage('Build') {
            steps {
                // NestJS 프로젝트 빌드
                sh 'npm run build'
            }
        }

        stage('Test') {
            steps {
                // 테스트 실행
                sh 'npm run test'
            }
        }

        // 배포 단계는 프로젝트 요구사항과 환경에 따라 다를 수 있으므로 여기서는 생략합니다.
        // stage('Deploy') {
        //     steps {
        //         // 배포 스크립트 실행
        //     }
        // }
    }

    post {
        always {
            // 항상 실행: 빌드 결과를 정리합니다.
            sh 'echo "Cleaning up..."'
        }
        success {
            // 성공 시 실행
            sh 'echo "Build succeeded."'
        }
        failure {
            // 실패 시 실행
            sh 'echo "Build failed."'
        }
    }
}