pipeline {
  agent { label 'lev' }
  environment {
    SW_VERSION='0.1'
    SW_BUILD_VERSION="${env.SW_VERSION}.${env.BUILD_NUMBER}"
  }
  stages {

    stage ('Extract: Master') {
      when {

        anyOf {
          branch 'master'
          branch 'develop'
	        branch 'preprod'
        }

      }
      steps {
        sh 'env'
        echo 'Building lev test..'

      }
    }    

  }
  post {
    always {
      junit 'eig-data-service/build/test-results/**/**.xml'
      jacoco()
    }
  }
}
