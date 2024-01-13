pipeline {
    agent {
        label { 'MAVEN' }
    }
    options { timeout(time: 30, unit: 'MINUTE') }
    triggers { pollSCM('* * * * *') }
    stages {
        stage('git') {
            git url: 'https://github.com/Hitansu26/spring-petclinic.git'
                branch: 'dev'
        }
        stage('build') {
            sh 'mvn clean package'
        }
    }
}