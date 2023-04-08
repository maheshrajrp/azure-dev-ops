podTemplate(yaml: readTrusted('./jenkins-cloud/pod.yml')) {

  node(POD_LABEL) {
    stage('Build a Maven project') {
      container('maven') {
        sh 'echo Hi'
        sh 'echo $POD_LABEL'
        sh 'touch hello-world.html'      
      }
    }
    stage('Test Stage 2') {
        container('maven') {
        sh 'ls'
        sh 'echo $POD_LABEL'
      }
    }
  }
}