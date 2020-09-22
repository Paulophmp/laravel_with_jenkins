pipeline {
  environment {
    registry = "https://github.com/Paulophmp/laravel_with_jenkins"
    registryCredential = 'dockerhub_id'
    dockerImage = ''
  }
  agent any
  stages {
    stage('Cloning Git') {
      steps {
        git 'https://github.com/Paulophmp/laravel_with_jenkins.git'
      }
    }
    stage('Building image') {
      steps{
        script {
          dockerImage = docker.build registry + ":$BUILD_NUMBER"
        }
      }
    }
    stage('Deploy Image') {
      steps{
        script {
          docker.withRegistry( '', registryCredential ) {
            dockerImage.push()
          }
        }
      }
    }
    stage('Remove Unused docker image') {
      steps{
        sh "docker rmi $registry:$BUILD_NUMBER"
      }
    }
  }
}
// node {
//   stage ('Build') {
//     git url: 'https://github.com/Paulophmp/laravel_with_jenkins'
//   }
//
// }





// node {
//   stage ('Build') {
//     git url: 'https://github.com/Paulophmp/laravel_with_jenkins'
//
//     // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
//   }
// }
