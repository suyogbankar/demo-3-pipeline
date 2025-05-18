pipeline {
    agent any
    tools {nodejs "mynodejs"}
    environment: {
        NODE_ENV = "production"
    }
    stages {
        stage('Hello') {
            steps {
                echo 'Hello World'
            }
        }
        stage('Dev') {
            steps {
                git 'https://github.com/suyogbankar/demo-3-pipeline.git'
                echo 'content of my file is'
                sh 'cat file1.txt'
            }
        }
        stage('node build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Save Artifacts') {
            steps {
                // archiveArtifacts artifacts: '**', followSymlinks: false
                archiveArtifacts artifacts: '*.txt', followSymlinks: false
            }
        }
        stage('Stage with Secret') {
            steps {
               withCredentials([string(credentialsId: 'mysecret', variable: 'production')]) {
                echo  "${production}"
                }
            }
        }
    }
}