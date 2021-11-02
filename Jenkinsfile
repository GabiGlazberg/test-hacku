pipeline {
    agent any

    stages {
        stage('Stage 1: handel files') {
            steps {
                dir('dir_1'){
                    echo "some text in file" | tee file{0..9}.txt
                }
            }
            steps {
                dir('dir_2'){
                    cp env.WORKSPACE/dir_1/** .
                    date | tee -a file{0..9}.txt
                }
            }
            steps {
                dir('dir_3'){
                    cp env.WORKSPACE/dir_2/** .
                    chmod 0444 ./
                }
            }
        }
        stage('Build Nginx') {
            steps {
                dir('nginx'){
                    docker run --name nginx -v env.WORKSPACE/dir_2:/usr/share/nginx/html:ro -d nginx
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying.... '
            }
        }
    }
}