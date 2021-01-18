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
			sh 'terraform apply -auto-approve'
		}
	}
    }
}
