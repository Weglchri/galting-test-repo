pipeline {
    agent any
    stages {
        stage("Maven build") {
             slackSend (color: '#FF0000', message: "Maven Build: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
	    steps {
                sh 'mvn -B clean package'
            }
        }
        stage("Gatling run") {
 slackSend (color: '#FF0000', message: "Gatling Run: Job '${env.JOB_NAME} [${env.BUILD_NUMBER}]' (${env.BUILD_URL})")
            steps {
                sh 'mvn gatling:test'
            }
            post {
                always {
                    gatlingArchive()
                }
            }
        }
    }
}

