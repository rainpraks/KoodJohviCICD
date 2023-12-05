pipeline {
    agent any

  tools {
  nodejs 'nodejs21'
}
environment {
        DEPLOY_DIR = "/kj_deployments/rain_${env.BRANCH_NAME}/"
    }

    stages {
        stage('checkout') {
            steps {
            git branch: 'main', poll: false, url: 'https://github.com/rainpraks/KoodJohviCICD'
        }
        }
        stage('Build') {
            steps {
           sh '''npm instal'''
           sh '''npm run build'''
            }
        }
        stage('copy') {
            steps {
            sh "mkdir -p ${DEPLOY_DIR}/"
            sh "cp -r dist/kood-johvi-cicd/browser/* ${DEPLOY_DIR}/"
            }
        }
    
        stage('discord') {
            steps {
                discordSend description: '', footer: '', image: '', link: '', result: '', scmWebUrl: '', thumbnail: '', title: '', webhookURL: 'https://discord.com/api/webhooks/1181572706446082100/NH6ErV3VR9mAo1E9fKqtRulJJBCHeQ0h4k3SdciGi_xE1XQIMv7dCz9WivgnD3JlcATb'
            }
        }
    }
    
    
}
