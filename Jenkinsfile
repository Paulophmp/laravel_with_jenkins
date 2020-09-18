node{
   stage('SCM Checkout'){
     git 'https://github.com/Paulophmp/laravel_with_jenkins'
   }
   
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'Maven3', type: 'maven'
      sh "${mvnHome}/bin/mvn package"
   }
   
   stage('Email Notification'){
      mail bcc: '', body: '''Hi Welcome to jenkins email alerts
      Thanks
      Hari''', cc: '', from: '', replyTo: '', subject: 'Jenkins Job', to: 'paulo.mendes00@hotmail.com'
   }
}
