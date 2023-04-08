podTemplate(yaml: readTrusted('./jenkins-cloud/pod.yaml')) {

  node(POD_LABEL) {
    stage('Build a Maven project') {
      container('maven') {
        sh 'echo Hi'
        sh 'echo $POD_LABEL'
      }
    }
  }
}