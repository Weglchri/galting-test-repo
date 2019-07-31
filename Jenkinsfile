pipeline {
    agent any
    stages {
        stage("Maven build") {
	    steps {
                slackSend (color: '#FFFF00', message: "STARTED: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
                sh 'mvn -B clean package'
            }
        }
        stage("Gatling run") {
            steps {
                sh 'mvn gatling:test'
            }
            post {
                always {
                    gatlingArchive()
                    notifySlack()
                }
            }
        }
    }
}

