properties([pipelineTriggers([githubPush()])])
@Library('github.com/releaseworks/jenkinslib') _

withCredentials(["AWS_ACCESS_KEY_ID=AKIAXEQG34BCPTUWSG66", "AWS_SECRET_ACCESS_KEY=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", "AWS_DEFAULT_REGION=eu-west-3"]) {
    AWS("ec2 describe-instances")
}

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
