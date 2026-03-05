pipeline{
    agent any
    environment{
        IMAGE_NAME = 'ayeshadockerhub/trend-app'
        IMAGE_TAG = '1.0'
    }
    stages{
        stage('Docker Build'){
            steps{
              sh '''docker build -t $IMAGE_NAME:$IMAGE_TAG .
'''  
            }
        }
        
        stage ('Docker login & push the image'){
            steps{
                withCredentials([usernamePassword(credentialsId: 'dockerhubcreds', passwordVariable: 'DOCKER_PASSWORD', usernameVariable: 'DOCKER_USERNAME')]) {
    sh '''echo $DOCKER_PASSWORD |  docker login -u $DOCKER_USERNAME --password-stdin
'''
sh 'docker push $IMAGE_NAME:$IMAGE_TAG'

}
            }
        }
    }
}