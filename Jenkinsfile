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
                git url: 'https://github.com/SkAamer1111/game-of-life-fork.git',
                    branch: 'develop'

            }
        }
        stage('build the code') {
            steps {
                sh script: 'mvn package'
            
            }
        }
        stage('publish reports') {
            steps {
                archiveArtifacts artifacts: '**/gameoflife.jar'
                junit testResults: '**/surefire-reports/TEST-*.xml'
                
            }
        }

    }
}