pipeline {
    agent any
    stages {
        stage('preparing docker / CI') {
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
                            sh '''
                              uname -a
                              pwd
                              whoami
                              ls -la
                              npm i
                              ls -la
                            '''
                        }
                    }
                }
                stage ('Analyzing with SonarQube') {
                    steps {
                        sh 'echo "Running SonarQube..."'
                    }
                }
            }
        }
        stage('Deploy for feature/jenkins-cicd / CD') {
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
        stage('Deploy for development / CD') {
            when {
                branch 'dev'
            }
            stages {
                stage('Deploying in dev server') {
                    steps{
                        script {
                            sh 'echo "Deploying in dev server..."'                            
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