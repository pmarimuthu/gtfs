pipeline {
    agent any

    environment {
        // Use Jenkins Credentials (Secret Text) for your GitHub token
        GITHUB_TOKEN = credentials('github-pmarimuthu-token')
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: "https://${GITHUB_TOKEN}:x-oauth-basic@github.com/pmarimuthu/gtfs.git"
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Run Spring Boot') {
            steps {
                sh 'mvn spring-boot:run'
            }
        }
    }
}
