#!groovy

node {

    def mavenImg = docker.build('maven:3-alpine', '-v $HOME/.m2:/root/.m2 --network container:sonarqube')

    mavenImg.inside {
        stage('Build') {
            echo 'Building...'
            sh 'mvn -X clean'
        }
        stage('Scan') {
            echo 'Scanning...'
            sh 'mvn -X -DskipTests sonar:sonar'
        }
        stage('Test') {
            echo 'Testing...'
        }
        stage('Deploy') {
            echo 'Deploying...'
            sh 'mvn -X install'
        }
    }
}