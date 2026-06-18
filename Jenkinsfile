pipeline {

    agent any

    tools {
        maven 'maven'
    }

    environment {
        APP_NAME = "java-maven-app"
        DOCKER_IMAGE = "myapp:v1"
    }

    stages {

        // STEP 1 - Echo Commands
        stage('Echo Stage') {
            steps {
                echo 'Pipeline Started'
                echo 'Learning Jenkins Declarative Pipeline'
            }
        }


        // STEP 3 - Maven Build
        stage('Maven Build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

       

        // STEP 5 - Docker Build
        stage('Docker Build') {
            steps {
                sh 'docker build -t ${DOCKER_IMAGE} .'
            }
        }

        // STEP 6 - Deployment Stage
        stage('Deploy Stage') {
            steps {
                echo 'Deploying Application'
                sh 'docker run -d -p 8081:8080 ${DOCKER_IMAGE}'
            }
        }
    }

    // POST ACTIONS
    post {

        success {
            echo 'Pipeline Executed Successfully'
        }

        failure {
            echo 'Pipeline Failed'
        }

        always {
            echo 'Pipeline Execution Completed'
        }
    }
}
