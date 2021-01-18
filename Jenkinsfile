properties([pipelineTriggers([githubPush()])])

pipeline {
    node {
  	stage("List S3 buckets") {
   		withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'aws-key', usernameVariable: 'AKIAXEQG34BCPTUWSG66', passwordVariable: 'DFfc8eP02LZN0pSmPj83a8DoXyqzSh5rX3Gumvz0']]) {
        		AWS("--region=eu-west-3")
    		}
   	}
    }

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
