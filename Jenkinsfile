pipeline{
	agent any
	stages{
	    stage('trivy'){
			steps{
				withGradle{
					sh 'trivy --format json --output trivy-results.json filesystem . '
				}
			}
			post{
				always{
					
				 	recordIssues enabledForFailure: true,
					tool: trivy(pattern: 'trivy-results.json')
				}
			}
		}
	}
}
