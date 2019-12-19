pipeline {
    agent  any
       
    options {
        disableConcurrentBuilds()
    }
    environment {
        ROS1_SOURCE_PATH = "/opt/ros/melodic/setup.bash"
        ROS1_WS_PATH = "/home/jenkins/catkin_ws"
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
            emailext body: 'test', recipientProviders: [developers()], subject: 'Build Failed ${env.BUILD_URL}'
        }
    }
}

