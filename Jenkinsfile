podTemplate(yaml: readTrusted('./jenkins-cloud/pod.yml')) {

    environment {
        IMAGE_TAG = "maheshrajiris.azurecr.io/iris/iris-ui:${env.BRANCH_NAME}"
    }

  node(POD_LABEL) {

    stage('Checkout SCM') {
      checkout scm
    }
    stage('Prepare') {
        container('node') {
        sh "echo $IMAGE_TAG"
      }
    }
    stage('Build') {
        container('node') {
        sh 'ls'
        sh 'npm install'
        sh 'npm run build'
      }
    }
    stage('Publish') {
      container('kaniko') {
        sh 'ls /kaniko'
        sh 'ls /kaniko/.docker'
        sh "/kaniko/executor --dockerfile `pwd`/Dockerfile --context `pwd` \
            --destination $IMAGE_TAG \
            --skip-tls-verify --insecure"
      }
    }
  }
}