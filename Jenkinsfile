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
                script {
			    // Let's clone the source
                git credentialsId: '976c8a11-ab25-4ef8-9344-39d3de2f67db', url: 'https://github.com/devops478/java-rest-api-calculator.git'
            }
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
