pipeline {
    agent any

    stages {
        stage('Stage 1: handel files') {
            steps {
                dir('dir_1'){
                    sh "echo some text in file | tee file{0..9}.txt"
                    sh "ls"
                }
            }
            steps {
                dir('dir_2'){
                    sh "cp env.WORKSPACE/dir_1/** ."
                    sh "date | tee -a file{0..9}.txt"
                    sh "ls"
                }
            }
            steps {
                dir('dir_3'){
                    sh "cp env.WORKSPACE/dir_2/** ."
                    sh "chmod 0444 ./"
                }
            }
        }
        stage('Build Nginx') {
            steps {
                dir('nginx'){
                    sh "docker run --name nginx -v env.WORKSPACE/dir_2:/usr/share/nginx/html:ro -d nginx"
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