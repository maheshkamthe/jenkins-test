pipeline {
    agent {
        docker { image 'maven:3.9-sapmachine' }
    }
    stages {
        stage('Source') {
            steps {
                sh 'mvn --version'
                sh 'git --version'
                git branch: 'main',
                    url: 'https://github.com/maheshkamthe/jenkins-test.git'
            }
        }
        stage('Clean') {
            steps {
                dir("${env.WORKSPACE}/Ch04/04_03-docker-agent"){
                    sh 'mvn clean'
                }
            }
        }
        stage('Test') {
            steps {
                dir("${env.WORKSPACE}/Ch04/04_03-docker-agent"){
                    sh 'mvn test'
                }
            }
        }
        stage('Package') {
            steps {
                dir("${env.WORKSPACE}/Ch04/04_03-docker-agent"){
                    sh 'mvn package -DskipTests'
                }
            }
        }
    }
}
