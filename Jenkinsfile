pipeline {
    agent any

    stages {
        stage ('Compile Stage') {

            steps {
                withMaven(maven : 'M3') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Testing Stage') {

            steps {
                withMaven(maven : 'M3') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Deployment Stage') {
            steps {
                withMaven(maven : 'M3') {
                    sh 'mvn deploy'
                }
            }
        }
    }
    pipeline {
        agent any
        stages {
            stage('Send Email') {
                steps {
                node ('master'){
                    echo 'Send Email'
                }
            }
            }
        }
        post { 
            always { 
                echo 'I will always say Hello!'
            }
            aborted {
                echo 'I was aborted'
            }
            failure {
                mail to: 'paulo.mendes00@hotmail.com',
                subject: "Failed Pipeline: ${currentBuild.fullDisplayName}",
                body: "Something is wrong with ${env.BUILD_URL}"
            }
        }
    }
}
