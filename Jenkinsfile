pipeline {
    agent any
    
    environment {
        DOCKER_IMAGE = 'flask-app'
        DOCKER_TAG = 'latest'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build and Test') {
            steps {
                script {
                    // 使用docker容器运行Python测试
                    docker.image('python:3.9').inside {
                        sh 'pip install -r requirements.txt'
                        sh 'pip install pytest'
                        sh 'python -m pytest tests/'
                    }
                }
            }
        }
        
        stage('Build Docker Image') {
            steps {
                script {
                    // 构建应用Docker镜像
                    sh 'docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} .'
                }
            }
        }
        
        stage('Deploy') {
            steps {
                script {
                    // 部署应用
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
