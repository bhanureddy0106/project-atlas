pipeline {
    agent any

    tools {
        maven 'Maven-3.9.12'
        jdk 'JDK-17'
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/bhanureddy0106/project-atlas.git', branch: 'main'
            }
        }

        stage('Build & Test') {
            steps {
                bat 'cd atlas-app && mvn clean test package'
            }
        }
    }

    post {
        always {
            junit 'atlas-app/target/surefire-reports/*.xml'
            archiveArtifacts 'atlas-app/target/*.jar'
        }
    }
}
