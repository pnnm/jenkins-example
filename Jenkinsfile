pipeline {
    environment {
    registry = "swapnaponnam1/docker-test"
    registryCredential = "docker-hub"
  }
    agent any

    stages {
       
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean install'
                }
            }
        }
         stage('Push image to private docker-hub') {
      steps {
        withDockerRegistry([credentialsId: 'docker-hub', url: "https://index.docker.io/v1/"]) {
         
          
        }
      }
    }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn test'
                }
            }
        }

    }
}
