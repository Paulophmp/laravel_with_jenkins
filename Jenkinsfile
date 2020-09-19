pipeline {

        environment {
        registry = "paulinho/laravel-kubernetes"
        registryCredential = 'dockerhub_id'
        dockerImage = ''
        }
        agent any

stages {
    stage('Cloning our Git') {
        steps {
            git 'https://github.com/Paulophmp/laravel_with_jenkins'
        }
    }

    stage('Building our image') {
        steps{
            script {
                dockerImage = docker.build registry + ":$BUILD_NUMBER"
            }
        }
    }

    stage('Deploy our image') {
        steps{
            script {
                  docker.withRegistry( '', registryCredential ) {
                       dockerImage.push()
                  }
            }
        }
    }

    stage('Cleaning up') {
            steps{
                sh "docker rmi $registry:$BUILD_NUMBER"
            }
        }
    }
}





// node {
//   stage ('Build') {
//     git url: 'https://github.com/Paulophmp/laravel_with_jenkins'
//
//     // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
//   }
// }
