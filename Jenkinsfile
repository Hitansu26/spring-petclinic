pipeline {
    agent { 
        label { 'MAVEN' }
    }
    options { timeout(time: 30, unit: 'MINUTE' ) }
    triggers {
        pollSCM { ('* * * * *') }
    }
    stages {
        stage('GIT') {
            steps{
                git url: 'https://github.com/Hitansu26/Jenkins-Project.git'
                    branch: 'main'
            }
        }
        stage('build') {
            steps{
                sh 'mvn clean package'
            }
        }
    }
}