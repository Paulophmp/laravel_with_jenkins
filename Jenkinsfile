node{
   stage('SCM Checkout'){
     git 'https://github.com/Paulophmp/laravel_with_jenkins'
   }

   stage('Email Notification'){
      mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      Thanks
      Hari''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'paulo.mendes00@hotmail.com'
   }
}





// node {
//   stage ('Build') {
//     git url: 'https://github.com/Paulophmp/laravel_with_jenkins'
//
//     // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
//   }
// }
