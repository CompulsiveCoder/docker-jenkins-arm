pipeline {
    agent any
    triggers {
        pollSCM 'H/2 * * * *'
    }
    stages {
        stage('Build') {
            steps {
                sh 'sh build.sh'
            }
        }
        stage('Login') {
            steps {
                sh 'docker login -u $DOCKERHUB_USERNAME -p $DOCKERHUB_PASSWORD'
            }
        }
        stage('Tag') {
            steps {
                sh 'sh tag.sh'
            }
        }
        stage('Push') {
            steps {
                sh 'sh push.sh'
            }
        }
    }
    post {
        always {
            cleanWs()
        }
    }
}
