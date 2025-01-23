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
        
        stage('Test') {
            steps {
                // 使用docker run命令执行测试
                sh '''
                    docker run --rm \
                        -v $WORKSPACE:/app \
                        -w /app \
                        python:3.9 \
                        /bin/bash -c "pip install -r requirements.txt && pip install pytest && python -m pytest tests/"
                '''
            }
        }
        
        stage('Build Docker Image') {
            steps {
                // 构建应用Docker镜像
                sh 'docker build -t ${DOCKER_IMAGE}:${DOCKER_TAG} .'
            }
        }
        
        stage('Deploy') {
            steps {
                // 部署应用
                sh 'docker-compose up -d --build web'
            }
        }
    }
    
    post {
        always {
            cleanWs()
        }
    }
}
