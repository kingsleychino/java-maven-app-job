def gv

pipeline {
    agent any

    tools {
        maven 'maven-3.9'
    }

    stages {
        stage("init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        
        stage("build jar") {
            steps {
                script {
                    gv.buildjar()
                }
            }
        }

        stage("build image") {
            steps {
                script {
                    echo "building the image..."
                    gv.buildImage()
                }
            }
        }
        
        stage("deploy") {
            steps {
                script {
                    echo "deploying the application..."
                }
            }
        }
    }
}
