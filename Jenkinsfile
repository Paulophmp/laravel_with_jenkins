node {

    checkout scm

    // Pega o commit id para ser usado de tag (versionamento) na imagem
    sh "git rev-parse --short HEAD > commit-id"
    tag = readFile('commit-id').replace("\n", "").replace("\r", "")

    // configura o nome da aplicação, o endereço do repositório e o nome da imagem com a versão
    appName = "default"
    registryHost = "paulinho/laravel-kubernetes"
    imageName = "${registryHost}${appName}:${tag}"

    // Configuramos os estágios

    stage "Build"

        def customImage = docker.build("${imageName}")

    stage "Push"

        customImage.push()


    stage "Deploy PROD"

        input "Deploy to PROD?"
        customImage.push('latest')
        sh "helm install --generate-name  ./meu-helm"
        sh "kubectl set image deployment app app=${imageName} --record"
        sh "kubectl rollout status deployment/app"
}