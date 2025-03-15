pipeline {
    agent any
   
    stages {
        stage('Clone Repository') {
            steps {
                // Clean workspace before starting
                cleanWs()
               
                // Echo the current directory for verification
                sh 'echo "Current directory: $PWD"'
               
                // Clone the repository into workspace instead of Jenkins home
                sh '''
                    if [ -d "my_python_project" ]; then
                        echo "Directory already exists, removing it"
                        rm -rf my_python_project
                    fi
                   
                    git clone https://github.com/jineshranawatcode/my_python_project.git
                   
                    echo "Repository cloned successfully!"
                    ls -la my_python_project
                '''
            }
        }
       
        stage('Verify Clone') {
            steps {
                // Verify in the workspace where we have permissions
                sh '''
                    cd my_python_project
                    ls -la
                    git status
                '''
            }
        }
    }
   
    post {
        success {
            echo 'Repository cloned successfully to workspace!'
        }
        failure {
            echo 'Failed to clone repository.'
        }
    }
}
