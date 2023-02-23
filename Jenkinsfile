pipeline{
	agent any
	stages{
		stage("Pull Latest Image"){
			steps{
				bat "docker pull testsms/selenium-docker"
			}
		}
		stage("Start Grid"){
			steps{
				bat "docker-compose up -d hub chrome firefox"
			}
		}
		stage("Run Test"){
			steps{
				bat "docker-compose up bookflight1 bookflight"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'results/**'
			bat "docker-compose down"
					}
	}
}


