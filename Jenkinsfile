podTemplate(yaml: """
apiVersion: v1
kind: Pod
spec:
  activeDeadlineSeconds: 304
  containers:
  - name: nodejs
    image: node:6-alpine
    command: ['cat']
    tty: true
"""
  ) {

  node(POD_LABEL) {
    stage('Build nodejs') {
      sh "echo Workspace dir is ${pwd()}"  
      checkout scm
      container('nodejs') {
        sh 'npm install'
      }
    }
  }
}
