pipeline{
    agent any
    stages{
        stage("Sonar Quality Check"){
            agent {
                docker {
                    image 'openjdk:11'
                }
               }
            steps{
               script{
                withSonarQubeEnv(credentialsId: 'sonarsever') {
                    script{
                        sh "chown +x gradlew"
                        sh "./gradlew sonarqube"
                    }
                }
               }
            }
            
        }  
    }
    post{
        always{
            echo "success"
        }
        
    }
}