pipeline {
    agent none

    stages {
        stage('Build') {
            agent {
                label "master"
            }
            tools {
              maven "MAVEN3.8.1"
            }
            steps {
                git 'https://github.com/devops478/java-rest-api-calculator'
                sh 'mvn clean compile'
                // bat '.\\mvnw clean compile'
            }
        }
        stage('Test') {
            agent {
                label "master"
            }
            steps {
                sh 'mvn test'
                // bat '.\\mvnw test'
            }

            post {
                always {
                    junit '**/target/surefire-reports/TEST-*.xml'
                }
            }
        }
    }
}
