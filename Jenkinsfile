properties([pipelineTriggers([githubPush()])])
@Library('github.com/releaseworks/jenkinslib') _

withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'ynov_22', usernameVariable: 'AKIAXEQG34BCPTUWSG66', passwordVariable: 'DFfc8eP02LZN0pSmPj83a8DoXyqzSh5rX3Gumvz0']]) {
        AWS("--region=eu-west-1 s3 ls")
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
