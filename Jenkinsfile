#!groovy

/* Requires the Docker Pipeline plugin */
node {
    checkout scm
    docker.image('maven:3-alpine').inside('--network container:sonarqube -v /root/.m2:/root/.m2') {
//    docker.image('maven:3-alpine').inside('--network container:sonarqube -v $HOME/.m2:/root/.m2 -w /usr/src/maven') {
        stage('Build') {
            echo 'Building...'
            sh 'mvn -version'
            sh 'mvn -X -B -DskipTests clean package'
        }
        stage('Scan') {
            echo 'Scanning...'
//            sh 'mvn -X -DskipTests sonar:sonar'
        }
        stage('Test') {
            echo 'Testing...'
        }
        stage('Deploy') {
            echo 'Deploying...'
//            sh 'mvn -X install'
        }
    }
}