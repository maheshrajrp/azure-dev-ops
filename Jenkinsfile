podTemplate(yaml: readTrusted('./jenkins-cloud/pod.yml')) {

  node(POD_LABEL) {
    stage('Checkout SCM') {
      checkout scm
    }
    stage('Check Auth') {
      container('kaniko') {
        sh 'cat /kaniko/.docker/config.json'
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
        sh '/kaniko/executor --dockerfile `pwd`/Dockerfile --context `pwd` \
            --destination maheshrajiris.azurecr.io/iris/iris-ui:nightly \
            --skip-tls-verify --insecure '
      }
    }
  }
}