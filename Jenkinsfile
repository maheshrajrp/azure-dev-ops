podTemplate(yaml: readTrusted('./jenkins-cloud/pod.yml')) {

  node(POD_LABEL) {
    stage('Checkout SCM') {
      checkout scm
    }
    stage('Build a Maven project') {
      container('node') {
        sh 'echo Hi'
        sh 'echo $POD_LABEL'
        sh 'touch hello-world.html'      
      }
    }
    stage('Build') {
        container('node') {
        sh 'ls'
        sh 'npm install'
        sh 'npm run build'
      }
    }
  }
}