pipeline {
    agent any 
    environment {
    DOCKERHUB_CREDENTIALS = credentials('valaxy-dockerhub')
    }
    stages { 
        stage('SCM Checkout') {
            steps{
            git 'https://github.com/jsilaparasetti/Claims_Nov_28/claims.git'
            }
        }

        stage('Build docker image') {
            steps {  
                sh 'docker build -t jsilaparasetti/Claims_Nov_28/claims:latest .'

            }
        }
        stage('login to dockerhub') {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
      //  stage('push image') {
        //    steps{
               
          //      sh 'docker push valaxy/nodeapp:$BUILD_NUMBER'
            //}
        //}
}
post {
        always {
            sh 'docker logout'
        }
    }
}
