pipeline {
    agent any
    tools {nodejs "mynodejs"}
    environment {
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
            environment {
                NODE_ENV = "stage"
            }
            steps {
                // archiveArtifacts artifacts: '**', followSymlinks: false
                archiveArtifacts artifacts: '*.txt', followSymlinks: false
                // echo NODE_ENV
                echo "${env.NODE_ENV}" // safer way to print env variable
            }
        }
        stage('Stage with Secret') {
            steps {
               withCredentials([string(credentialsId: 'mysecret', variable: 'PRODUCTION_SECRET')]) {
                echo  "${PRODUCTION_SECRET}"
                script {
                    println "The secret value is : ${PRODUCTION_SECRET}"
                }                
            }
        }
    }
}