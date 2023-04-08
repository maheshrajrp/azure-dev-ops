podTemplate(yaml: readTrusted('./jenkins-cloud/pod.yml')) {

  node(POD_LABEL) {
    stage('Checkout SCM') {
      checkout scm
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
        sh '/kaniko/executor --dockerfile=`pwd`/Dockerfile --context=`pwd` \
            --destination=`$destinationRepo` \
            --skip-tls-verify=true'
      }
    }
  }
}