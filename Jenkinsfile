
 stage('Checkout') {
    checkout([$class: 'GitSCM',
              userRemoteConfigs: [[url: 'ssh://git@github.com:Paulophmp/laravel_with_jenkins.git',
                                   credentialsId: 'dockerhub',
                                   name: 'origin',
                                   refspec: "+refs/heads/${branch}:refs/remotes/origin/${branch}",
                                  ]],
              branches: [[name: "*/${branch}"]],
              browser: [$class: 'GithubWeb',
                        repoUrl: 'https://github.com/Paulophmp/laravel_with_jenkins'],
              extensions: [[$class: 'AuthorInChangelog'],
                           [$class: 'CheckoutOption', timeout: 1],
                           [$class: 'CleanCheckout'],
                           [$class: 'CloneOption',
                            depth: 3,
                            honorRefspec: true,
                            noTags: true,
                            reference: '/var/lib/git/mwaite/bugs/jenkins-bugs-private.git',
                            shallow: true,
                            timeout: 3],
                           [$class: 'LocalBranch', localBranch: '**'],
                           [$class: 'PruneStaleBranch'],
                           [$class: 'SubmoduleOption',
                            disableSubmodules: false,
                            parentCredentials: true,
                            recursiveSubmodules: true,
                            reference: '/var/lib/git/mwaite/bin.git',
                            trackingSubmodules: false],
                           [$class: 'WipeWorkspace'],
                           ],
              gitTool: "Default", // JGit does not support submodules
             ])
  }



// node {
//   stage ('Build') {
//     git url: 'https://github.com/Paulophmp/laravel_with_jenkins'
//
//     // withMaven will discover the generated Maven artifacts, JUnit Surefire & FailSafe reports and FindBugs reports
//   }
// }
