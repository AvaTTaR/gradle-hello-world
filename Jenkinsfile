pipeline{
  agent {
    label 'slave1'
  }
  tools {
  gradle 'gradle4'
  }
  stages{
    stage('checkout'){
      steps{
          checkout scm
      }
  }
        stage('build'){
          steps{
           sh "gradle build"
          }
        }
    }
  post {
  success {
    addBadge icon: '', id: '', link: 'env.JOB_URL', text: 'OK'
  }
  unsuccessful {
    addBadge icon: '', id: '', link: 'env.JOB_URL', text: 'FAIL'
  }
}

}
