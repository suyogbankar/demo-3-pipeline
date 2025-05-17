pipeline {
    agent any
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
    }
}