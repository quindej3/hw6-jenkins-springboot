pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build with Maven') {
            steps {
                // run Maven inside the Spring Boot project folder
                dir('hw6-springboot') {
                    sh 'mvn -B clean package -DskipTests'
                }
            }
        }
    }

    post {
        success {
            // archive the built JAR from the subfolder
            archiveArtifacts artifacts: 'hw6-springboot/target/*.jar', fingerprint: true
        }
    }
}

