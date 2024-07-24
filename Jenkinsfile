pipeline {
    agent any
 
    environment {
        MAVEN_HOME = tool 'Maven - 3.9.0' // Ensure this matches your Maven tool name
    }
 
    stages {
        stage('Checkout') {
            steps {
                // Checkout code from GitHub repository
                git url: 'https://github.com/yaksh0210/training_jenkins_tasks.git', branch: 'main'
            }
        }
        
        stage('Build') {
            steps {
        
                script {
        
                    withEnv(["PATH+MAVEN=${MAVEN_HOME}\\bin"]) {
        
                        sh 'mvn clean package'
                    }
                }
            }
        }

 
        stage('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: '**/target/*.jar', allowEmptyArchive: true
            }
        }
    }
 
    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Pipeline succeeded.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}
