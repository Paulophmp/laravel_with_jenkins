pipeline {
    agent any
    stages {
        stage('checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: tagVersion]],
                          userRemoteConfigs: [[url: 'ssh://git@github.com:Paulophmp/laravel_with_jenkins.git',
                                               credentialsId: 'dockerhub']]
                        ])
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
