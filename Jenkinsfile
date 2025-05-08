pipeline {
    agent any
    environment {
        // 明确指定所有路径
        DOCKER_BIN = '/usr/local/bin/docker'
        DOCKER_SOCK = '/var/run/docker.sock'
    }
    stages {
        stage('Build') {
            steps {
                sh '''
                    echo "=== 环境验证 ==="
                    ${DOCKER_BIN} --version
                    ls -l ${DOCKER_SOCK}

                    echo "=== 执行构建 ==="
                    ${DOCKER_BIN} run --rm -v ${DOCKER_SOCK}:${DOCKER_SOCK} \
                        -v $PWD:/workspace maven:3-alpine \
                        mvn -f /workspace clean package
                '''
            }
        }
    }
}