#!/bin/bash
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
    stage('Unit tests'){
        steps{
        sh 'gradle test'
        }
    }
    stage('func-test'){
        steps{
            parallel(
                "First test" : {
                    sh "chmod 777 test-data/int-test.sh"
                    sh "test-data/int-test.sh build/libs/oto-gradle-1.0.jar AvaTTaR 'Hello Avattar!'"
                },
                "Second test" : {
                    sh "chmod 777 test-data/int-test.sh"
                    sh "test-data/int-test.sh build/libs/oto-gradle-1.0.jar avattar 'Hello Avattar!'"
                },
                "third step" : {
                    sh "chmod 777 test-data/int-test.sh"
                    sh "test-data/int-test.sh build/libs/oto-gradle-1.0.jar aVATTAR 'Hello Avattar!'"
                }
            )
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
