podTemplate(yaml: """
apiVersion: v1
kind: Pod
spec:
  containers:
  - name: nodejs
    image: node:6-alpine
    command: ['cat']
    tty: true
	activeDeadlineSeconds: 300
"""
  ) {

  node(POD_LABEL) {
    stage('Build nodejs') {
      container('nodejs') {
        sh 'npm install'
      }
    }
  }
}