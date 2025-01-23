pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'flask-app'
        DOCKER_TAG = 'latest'
    }
    
    stages {
        stage('Setup Python') {
            steps {
                sh 'curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py'
                sh 'python3 get-pip.py'
                sh 'pip3 install pytest'
            }
        }

        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Install Dependencies') {
            steps {
                sh 'pip3 install -r requirements.txt'
            }
        }
        
        stage('Test') {
            steps {
                sh 'python3 -m pytest tests/'
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    sh 'docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} .'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    sh 'docker-compose up -d --build web'
                }
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
