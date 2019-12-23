pipeline {
    agent {
	label 'jenkins-sootballs-melodic-ci'
    }
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
            emailext body: '$DEFAULT_CONTENT', recipientProviders: [developers()], subject: '$DEFAULT_SUBJECT'
        }
    }
}

