pipeline {
    agent {
        docker {
            image 'maven:3-alpine'
            args '-v $HOME/.m2:/root/.m2'
        }
    }
    environment {
        PATH = "/usr/local/bin:$PATH"  // 显式添加 Docker 路径
    }
    stages {
        stage('Check Docker') {
            steps {
                sh 'which docker && docker --version'
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
    }
}