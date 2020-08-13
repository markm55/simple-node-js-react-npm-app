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
    env:
    - name: CI
      value: true
"""
  ) {

  node(POD_LABEL) {
    stage('Build nodejs') {
      sh "echo Workspace dir is ${pwd()}"  
      checkout scm
      container('nodejs') {
        sh 'npm install -g grunt-cli bower'
        sh 'npm install'
		  withCredentials([usernamePassword(credentialsId: 'gitHub_eBreviaToken', passwordVariable: 'pass', usernameVariable: 'user')]) {
			sh 'bower login -t $pass'
			sh 'bower install --allow-root'
		  }
//		sh 'grunt serve'
//		sh 'grunt --help'
//		sh 'bower --help'
      }
    }
/*    stage('Test') {
      container('nodejs') {
        sh './jenkins/scripts/test.sh'
      }
    }
	stage('Deliver') {
      container('nodejs') {
        sh './jenkins/scripts/deliver.sh'
        input message: 'Finished using the web site? (Click "Proceed" to continue)'
        sh './jenkins/scripts/kill.sh'
      }
    } */
  }
}
