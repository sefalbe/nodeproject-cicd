pipeline {
    // environment {
    //    registry = "sefalbe/nginx-react-demo"
    //    registryCredential = 'dockerhub'
    // }
    //  agent {
    //     docker { image 'node:10.19.0' }
    // }
    stages {
        stage('Installing and analyzing') {
            stages {
                stage ('Install') {
                    steps {
                        script {
                            sh 'whoami'
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
                stage('Zipping files') { /*Optional*/
                    steps{
                        sh 'echo "Zipping files..."'
                    }
                }
                stage('Deploy Website') {
                    steps{
                      sh 'echo "Deploying website..."'                        
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