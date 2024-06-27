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
                sh 'docker build -t charan-jenkins-hellow-world::${BUILD_NUMBER} .'
            }
        }

        stage('Docker Push') {
            steps {
               echo "Docker Push"
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
