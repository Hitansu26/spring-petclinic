pipeline {
    agent { label 'MAVEN' 'JDK_17' }
    option { 
        ( time: 30, unit: 'MINUTES') 
    }
    tiggers {
        pollSCM('* * * * *')
    }
    stages{
        stage('git') {
            steps {
                git url: 'https://github.com/spring-projects/spring-petclinic.git'
                branch: 'main'
            }
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
        }
    }
}