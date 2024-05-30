pipeline {
    agent any
    options {
        timeout (time:30, unit: 'MINUTES')
    }
    tools {
        jdk 'JDK_8'
        maven 'maven'
    }
    triggers {
        pollSCM ('H * * * *')
    }
    parameters {
        choice (name: 'GOAL' , choices:['validate','compile','test','package','install','deploy'])
    }
    stages {
        stage ('clone'){
            steps{
                git url: 'https://github.com/wakaleo/game-of-life.git',
                    branch: 'practice'
            }
        }
        stage ('build the code') {
            steps {
                sh "mvn ${params.GOAL}"
            }
        }
        stage ('reports'){
            steps{
                archiveArtifacts artifacts: '**/gameoflife.war'
                junit testResults: '**/surefire-reports/TEST-*.xml'  
            }
        }
    }

}
