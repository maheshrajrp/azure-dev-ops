podTemplate(containers: [
  containerTemplate(name: 'maven', image: 'maven:3.8.1-jdk-8', command: 'sleep', args: '99d')
  ]) {

  node(POD_LABEL) {
    stage('Build a Maven project') {
      container('maven') {
        sh 'echo Hi'
        sh 'echo $POD_LABEL'
      }
    }
  }
}