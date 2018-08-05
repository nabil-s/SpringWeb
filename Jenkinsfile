#!groovy

node {
//    docker.image('maven:3-alpine').inside('-v /root/.m2:/root/.m2 --network container:sonarqube') {
    docker.image('maven:3-alpine').inside('-v "$(pwd)":/usr/src/maven --network container:sonarqube') {

        stage('Build') {
            echo 'Building...'
            sh 'mvn -version'
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