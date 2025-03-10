pipeline {
    agent any
    
    stages {
        stage('Build') {
            steps {
                script {
                    sh 'g++ -o my_program main.cpp'
                }
            }
        }

        stage('Test') {
            steps {
                script {
                    sh './my_program > output.txt'
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    sh 'echo Deploying application...'
                }
            }
        }
        
        stage('Create and Push C++ File') {
            steps {
                script {
                    sh '''
                    echo '#include<iostream>\nusing namespace std;\nint main() { cout << "Hello, World!"; return 0; }' > new_file.cpp
                    git add new_file.cpp
                    git commit -m "Added new C++ file" || echo "No changes to commit"
                    git push origin main
                    '''
                }
            }
        }
    }
    
    post {
        failure {
            echo 'Pipeline failed'
        }
    }
}
