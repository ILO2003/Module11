pipeline {
    agent any
    tools{
        maven 'maven-3.9'
    }
    stages {
        stage("build jar") {
            steps {
                script {
                    echo "building the application ..."
                    sh 'mvn package'
                }
            }
        }
        stage("build image") {
            steps {
                script {
                    echo "building the docker image ..."
                    withCredentials([usernamePassword(credentialsId: 'docker-hub-repo', passwordVariable: 'PASSWORD', usernameVariable: 'USERNAME')]){
                        sh 'docker build -t ilo2003/testing:jma-2.0 .'
                        sh 'echo $PASS | docker login -u $USER --password-stdin'
                        sh 'docker push ilo2003/testing:jma-2.0'
                    }
                }
            }
        }
         stage("deploy") {
            steps {
                script {
                    echo "deploying the application ..."
                }
            }
        }
    }
}
