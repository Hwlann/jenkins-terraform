properties([pipelineTriggers([githubPush()])])

pipeline {
    agent { 
      docker {
        image 'hashicorp/terraform'
        args  '--entrypoint='
      }
    }
    
    stages {
	
	stage('init') {
		steps {
			sh 'terraform init'
		}
	}
	stage('plan') {
		steps {
			sh 'terraform plan'
		}
	}
	stage('apply') {
		steps {
			sh 'terraform apply -auto-approve'
		}
	}
    }
}
