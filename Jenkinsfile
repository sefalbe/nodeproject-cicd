pipeline {
    agent { docker { image 'node:14-alpine' } }
    stages {
        stage('build') {
            steps {
                sh 'npm --version'
            }
        }
        stage('test') {
          when {
            branch 'feature/jenkins-cicd'
          }
          steps {
            sh 'echo "Hola feature/jenkins-cicd"'
          }
        }
    }
}