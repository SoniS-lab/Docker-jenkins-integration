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
				bat "docker-compose up bookflight bookflight1"
			}
		}
	}
	post{
		always{
			archiveArtifacts artifacts: 'D:\Docker Tech Talk\Selenium Grid demo\results/**'
			bat "docker-compose down"
			bat "rmdir /s /q output "
		}
	}
}


