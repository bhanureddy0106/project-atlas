pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'JDK'
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
