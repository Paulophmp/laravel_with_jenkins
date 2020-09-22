node ('Build'){
  stage 'sanity check'
  sh 'echo sanity check'
  stage 'checkout other repository'
  checkout([
    $class: 'GitSCM', branches: [[name: '*/master']],
    userRemoteConfigs: [[url: 'https://github.com/Paulophmp/laravel_with_jenkins.git', credentialsId: 'dockerhub']]
  ])
  stage 'log results'
  sh 'echo result = OK'
 }



// node {
//   stage ('Build') {
//     git url: 'https://github.com/Paulophmp/laravel_with_jenkins'
//
//     // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
//   }
// }
