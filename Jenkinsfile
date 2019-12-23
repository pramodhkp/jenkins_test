pipeline {
    agent  any
       
    options {
        disableConcurrentBuilds()
    }
    environment {
        ROS1_SOURCE_PATH = "/opt/ros/melodic/setup.bash"
    }
    stages {
        stage('Test Parallel') {
           steps {
               sh label: 'test', script: '''exit -1'''
           }
        }
    }
    post {
        failure {
            slackSend notifyCommitters: true, message: "Build failed - ${env.JOB_NAME} ${env.BUILD_NUMBER} (<${env.BUILD_URL}|Open>) <@pramodhkp>"
        }
    }
}

