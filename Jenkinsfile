pipeline {
    agent any
    stages {
        stage('preparing docker') {
            agent {
                docker { 
                    image 'node:10.19.0'
                    args '--entrypoint=\'\' -v ${PWD}:/usr/src/app -w /usr/src/app'
                    reuseNode true
                }
            }
            stages {
                stage ('Install') {
                    steps {
                        script {
                            sh 'npm i'
                        }
                    }
                }
                // stage ('Analyzing with SonarQube') {
                //     steps {
                //         sh 'npm run build'
                //     }
                // }
            }
        }
        stage('Deploy for feature/jenkins-cicd') {
            when {
                branch 'feature/jenkins-cicd'
            }
            stages {
                stage('Deploying in server') {
                    steps{
                        script {
                            sh 'echo "Deploying in server..."'
                        }
                    }
                }                
            }
        }
        stage('Clean') {
            steps {
                deleteDir()
            }
        }
    }
}