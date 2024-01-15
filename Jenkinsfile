pipeline {
    agent { label  'MAVEN' }
    options { timeout(time: 30, unit: 'MINUTES') }
    triggers { 
        pollSCM('* * * * *') 
    }
    stages {
        stage('git') {
            steps {
                git url: 'https://github.com/Hitansu26/spring-petclinic.git', 
                    branch: 'dev'
            }
           
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
            }
            
        }
    }
}