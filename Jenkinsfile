pipeline {
  agent {
    docker {
      image "bryandollery/terraform-packer-aws-alpine"
      args "-u root --entrypoint=''"
    }
  }
  environment {
    CREDS = credentials('6c22797b-6e23-4779-984c-c18d46aade6b')
        AWS_ACCESS_KEY_ID="${CREDS_USR}"
        AWS_SECRET_ACCESS_KEY="${CREDS_PSW}"
        OWNER= "manar"
        TF_NAMESPACE="where-is-manar"
        PROJECT_NAME="web-server"
         AWS_PROFILE="kh-labs"
  }
  stages {
      stage("build") {
          steps {
              sh 'make init'
	      sh 'make plan'
          }
      }
	  //testing comments
      stage("release") {
          steps {
              sh 'make apply'
              sh 'cat ip_address.txt'
          }
      }
  }
}
