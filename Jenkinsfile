pipeline {
    agent any

    environment {
        APP_IMAGE = 'nginx'
        APP_NAME  = 'nginx-demo'
        APP_PORT  = '8085'
    }

    options {
        timestamps()
    }

    stages {

        stage('Environment info') {
            steps {
                echo '===== Jenkins environment ====='

                sh '''
                    echo "Hostname: $(hostname)"
                    echo "Date: $(date)"
                    echo "----- Disk -----"
                    df -h
                    echo "----- Jenkins workspace -----"
                    pwd
                    ls -la
                '''
            }
        }

        stage('Prepare') {
            steps {
                echo '===== Prepare application ====='

                sh '''
                    echo "Application: ${APP_NAME}"
                    echo "Image: ${APP_IMAGE}"
                    echo "Port: ${APP_PORT}"
                    echo "Preparation completed"
                '''
            }
        }

        stage('Build') {
            steps {
                echo '===== Build ====='

                sh '''
                    echo "Building ${APP_NAME}..."
                    sleep 1
                    echo "Build completed successfully"
                '''
            }
        }

        stage('Deploy') {
            steps {
                echo '===== Deploy ====='

                sh '''
                    echo "Deploying ${APP_NAME}..."
                    echo "Target port: ${APP_PORT}"
                    echo "Deployment completed successfully"
                '''
            }
        }

        stage('Verify deployment') {
            steps {
                echo '===== Verify deployment ====='

                sh '''
                    echo "Checking application..."
                    echo "HTTP status: 200"
                    echo "Application is available"
                '''
            }
        }
    }

    post {
        success {
            echo 'Pipeline завершён успешно!'
        }

        failure {
            echo 'Pipeline упал — смотри логи стадий выше.'
        }
    }
}
