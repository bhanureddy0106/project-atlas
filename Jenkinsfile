pipeline {
    agent any

    tools {
        maven 'Maven3'  // Match the exact name you used
        jdk 'JDK'       // Match the exact name you used
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
            // Make sure this is inside 'node' context
            junit 'atlas-app/target/surefire-reports/*.xml'
            archiveArtifacts 'atlas-app/target/*.jar'
        }
    }
}
