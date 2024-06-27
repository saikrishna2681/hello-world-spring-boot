pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building...'
                sh 'mvn clean install'
            }
        }

        stage('Docker build') {
            steps {
                echo 'Testing...'
                sh 'docker build -t charan-jenkins-hellow-world:${BUILD_NUMBER} .'
            }
        }
        
        stage('Docker login') {
            steps {
                echo 'Testing...'
                sh 'acr login -udeploymentpocfe.azurecr.io -piGLi5J5tftySSyA8SozT+QlcOPfd0bzxQZ718zilEs+ACRAkX8AH'
            }
        }
        
        stage('Docker Push') {
            steps {
                sh "docker tag charan-jenkins-hellow-world:${BUILD_NUMBER} deploymentpocfe.azurecr.io/charan-jenkins-hellow-world:${BUILD_NUMBER}"
                sh "acr push deploymentpocfe.azurecr.io/charan-jenkins-hellow-world:${BUILD_NUMBER}"
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            cleanWs()
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
