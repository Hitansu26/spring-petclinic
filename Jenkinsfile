pipeline {
    agent any
    options { timeout(time: 30, unit: 'MINUTES') }
    triggers { 
        pollSCM('* * * * *') 
    }
    stages {
        stage('git') {
            steps {
                git url: 'https://github.com/Hitansu26/Springpetclinic_project.git', 
                    branch: 'main'
            }
           
        }
        stage('build') {
            steps {
                sh 'mvn clean package'
                withSonarQubeEnv(installationName: 'sonar-cloud', credentialsId: 'sonat-token') {
                   sh  'mvn clean verify sonar:sonar -Dsonar.host.url=https://sonarcloud.io -Dsonar.organization=pet-clinic24 -Dsonar.projectKey=pet-clinic24_test'
                }
            }
        post {
            success {
                archiveArtifacts artifacts: '**/spring-petclinic-*.jar'
                junit testResults: '**/TEST-*.xml' 
            }
        }
        }
    }
}