#!groovy

node {
    // This displays colors using the 'xterm' ansi color map.
    ansiColor('xterm') {
        // Just some echoes to show the ANSI color.
        stage "\u001B[31mI'm Red\u001B[0m Now not"
    }
    docker.image('maven:3-alpine').inside('--network container:sonarqube -v /root/.m2:/root/.m2') {
//    docker.image('maven:3-alpine').inside('--network container:sonarqube -v $HOME/.m2:/root/.m2 -w /usr/src/maven') {
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