pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'maven_3_5_0') {
                    sh 'mvn clean install'
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

 stage('Push image to private docker-hub') {
      steps {
        withDockerRegistry([credentialsId: 'docker-hub', url: "https://index.docker.io/v1/"]) {
          sh 'sudo docker login https://index.docker.io/v1/ -u=swapnaponnam1 -p=Password2'
          sh 'sudo /usr/bin/docker push swapnaponnam1/jenkins-example:latest'
        }
      }
    }
    }
}
