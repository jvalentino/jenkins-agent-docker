pipeline {
 agent { label 'docker' }

  stages {
    
    stage('Publish') {
      steps {
        withCredentials([usernamePassword(
        credentialsId: 'dockerhub', 
        passwordVariable: 'DOCKER_PASSWORD', 
        usernameVariable: 'DOCKER_USERNAME')]) {
            sh '''
                nohup dockerd &
                sleep 10
                docker build -t jvalentino2/jenkins-agent-docker .
                docker login --username $DOCKER_USERNAME --password $DOCKER_PASSWORD
                docker tag jvalentino2/jenkins-agent-docker:latest jvalentino2/jenkins-agent-docker:1.${BUILD_NUMBER}
                docker push jvalentino2/jenkins-agent-docker:1.${BUILD_NUMBER}
                cat /var/run/docker.pid | xargs kill -9 || true
            '''
        }
      }
    } // Publish

  }
}