pipeline {
  agent {
      kubernetes {
          yamlFile './jenkins-cloud/pod.yml'
      }
  }

  environment {
    IMAGE_TAG = "maheshrajiris.azurecr.io/iris/iris-ui:${env.BRANCH_NAME}"
  }
  stages {
    stage('Prepare') {
      steps {
        container('node') {
          sh 'ls'
          sh "echo $IMAGE_TAG"
        }
      }
    }
    stage('Build') {
      steps {
        container('node') {
          sh 'ls'
          sh 'npm install'
          sh 'npm run build'
        }
      }
    }
    stage('Publish') {
      steps {
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
}
