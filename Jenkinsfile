#!groovy

node {
    docker.image('maven:3-alpine').inside('-v $HOME/.m2:/root/.m2 --network container:sonarqube') {
        echo 'PATH = $PATH'
        echo 'M2_HOME = $M2_HOME'
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