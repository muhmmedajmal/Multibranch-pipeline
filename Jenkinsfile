pipeline {
    agent any

    tools {
        maven 'my-maven'
    }

    environment {
        BRANCH_NAME = "${env.BRANCH_NAME}"
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean run'
            }
        }

        stage('Run') {
            steps {
                sh 'java -cp target/classes com.example.HelloApp'
            }
        }
    }

    post {
        always {
            echo "Pipeline completed for branch: ${env.BRANCH_NAME}"
        }
    }
}
