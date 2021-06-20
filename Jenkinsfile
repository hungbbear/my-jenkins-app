node {
    def commit_id
    stage('Preparation'){
        checkout scm
        sh "git rev-parse --short HEAD > .git/commit_id"
        commit_id = readFile('.git/commit-id').trim()
    }
    stage('Docker build/push'){
        docker.withRegisty('https://index.docker.io/v1/', 'dockerhub'){
            def app = docker.build("stirenbenzen/my-jenkins-cicd:${commit_id}", '.').push
        }
    }
}