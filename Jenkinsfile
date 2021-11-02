pipeline {
    agent {
        node {
            label 'test-slave'
            }
        }
        stages {
            stage('Stage 1: handel files') {
                steps {
                    dir('dir_1'){
                        sh "echo some text in file | tee file{0..9}.txt"
                    }
                }
            }
            stage('Copy files and add date to the text') {
                steps {
                    dir('dir_2'){
                        sh "cp -a ${WORKSPACE}/dir_1/. ."
                        sh "date | tee -a file{0..9}.txt"
                        sh "ls"
                    }
                }
            }
            stage('Copy files 3') {
                steps {
                    dir('dir_3'){
                        sh "cp  -a ${WORKSPACE}/dir_2/. ."
                        sh "chmod 0444 ./"
                    }
                }
            }
            stage('Build Nginx') {
                steps {
                    dir('nginx'){
                        sh "docker run --name nginx -v ${WORKSPACE}/dir_2:/usr/share/nginx/html:ro -d nginx"
                    }
                }
            }
        }
}