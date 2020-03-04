pipeline {
    agent any
    options {
        disableConcurrentBuilds()
        timeout(time: 30, unit: "MINUTES")
    }
    stages {
        stage("verification") {
            steps {
                sh "echo test verification stage"
                sh "docker-compose --version"
                sh "which docker-compose"
                sh "docker -v"
                sh "which docker"
            }
        }
        stage ("where are we") {
            steps {
                sh "ls"
                sh "pwd"
            }
        }
        stage ("build") {
            steps {
				dir("CDTestApi"){
					sh "echo start build"
					sh "docker-compose build"
					sh "echo succesfull build"
				}
            }
        }
        stage ("run") {
            steps {
				dir("CDTestApi") {
						sh "docker-compose up -d --force-recreate --remove-orphans"
					}
            }
        }

    }
}