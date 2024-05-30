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
            git url: 'https://github.com/wakaleo/game-of-life.git',
                branch: 'master'
        }
        stage ('build the code') {
            sh "mvn ${params.GOAL}"
        }
        stage ('reports'){
            archiveArtifacts artifacts: '**/gameoflife.war'
            junit testResults: '**/surefire-reports/TEST-*.xml'   
        }
    }
    post {
        success {
            mail from: 'jenkins@gmail.com',
                 to: 'mailtrapgmail.com',
                 body: 'you project is successfull',
                 subject: 'game of life',

        }
        failure{
            mail from: 'jenkins@gmail.com',
                 to: 'mailtrapgmail.com',
                 body: 'you project is failing',
                 subject: 'game of life',
        }
    }


}
