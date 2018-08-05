#!groovy

node {
//    docker.image('maven:3-alpine').inside('-v /root/.m2:/root/.m2 --network container:sonarqube') {
    docker.image('maven:3-alpine').inside('--network container:sonarqube -v "$(pwd)":/usr/src/maven -w /usr/src/maven') {

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