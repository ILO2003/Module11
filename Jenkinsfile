pipeline {
    agent any
    stages {
        stage("test") {
            steps {
                script{
                    echo 'Testing the application ....'
                }
            }
        }
        stage("build") {
            steps {
                script{
                    echo 'Building the application ....'
                }
            }
        }
         stage("deploy") {
            steps {
                script{
                    echo 'Deploying the application ....'
		    withKubeConfig([credentialsId: 'lke-credentials', serverUtl: 'https://347c8331-a359-4529-8997-d51eda9f8ad2.se-sto-1.linodelke.net']){
		    sh 'kubectl create deployment nginx-deployment --image=nginx'
		    }
                }
            }
        }
    }
}
