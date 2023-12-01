pipeline {
    agent { label 'practice'}
    option {
        timeout (time:30, unit: 'MINUTES')
    }
    triggers {
        pollSCM (* * * * *)
    }
    tools {
        jdk 'jdk-8'
        maven 'maven-3.9.3'
    }
    stages {
        stage('get the code') {
            steps {

            }
        }
        stage('build the code') {
            steps {

            }
        }
        stage('publish reports') {
            steps {
                
            }
        }

    }
}