pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                script {
                    echo "Building the application..."
                    sh "make -C main clean && make -C main hello_exec"
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    echo "Running tests..."
                    // Intentional error: Trying to execute a non-existent file
                    sh "./main/non_existent_exec"
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    echo "Deploying application..."
                    sh 'echo "Deployment successful!"'
                }
            }
        }
    }

    post {
        failure {
            echo "Pipeline failed"
        }
        success {
            echo "Pipeline completed successfully!"
        }
    }
}
