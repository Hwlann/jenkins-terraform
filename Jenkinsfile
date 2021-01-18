properties([pipelineTriggers([githubPush()])])

pipeline {
    agent { 
      docker {
        image 'hashicorp/terraform'
        args  '--entrypoint='
      }
    }
    
    stages {
	stage('aws-configure') {
		step {
			sh 'aws configure'
		}
	}
	stage('init') {
		step {
			sh 'terraform init'
		}
	}
	stage('plan') {
		step {
			sh 'terraform plan'
		}
	}
	stage('apply') {
		step {
			sh 'terraform apply -auto-approve'
		}
	}
    }
}
