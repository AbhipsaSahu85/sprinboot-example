pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                echo 'getting application from git'
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-cred', url: 'https://github.com/jacksontechtraining/samplespring']]])
            }
        }
        stage('Complie') {
            steps {
                echo 'compliling application'
                bat 'mvn compile'
            }
        }
        stage('Package') {
            steps {
                echo 'packaging the application'
                bat 'mvn package'
            }
        }
        stage('Deploy'){
            steps {
                echo 'geting dependency to deploy app'
                bat 'mvn install'
            }
        }
        stage('Test') {
            steps {
                echo 'testing the application'
                bat 'mvn test'
            }
        }
    }
}


