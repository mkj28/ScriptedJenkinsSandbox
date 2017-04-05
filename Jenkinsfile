properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '7', numToKeepStr: '50')), parameters([[$class: 'GitParameterDefinition', branch: '', branchFilter: '.*', defaultValue: '', description: 'Git Branch Or Tag', name: 'GITBRANCHORTAG', quickFilterEnabled: false, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'PT_BRANCH_TAG']]), pipelineTriggers([pollSCM('H/2 * * * *')])])

node {
    stage('Checkout') {
        git url: 'https://github.com/mkj28/ScriptedJenkinsSandbox.git'
        checkout scm
    }

    stage('User input') {
        input message: 'Select tag', parameters: [[$class: 'GitParameterDefinition', branch: '', branchFilter: '.*', defaultValue: '', description: 'Git Tag Description', name: 'gitTag', quickFilterEnabled: true, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'PT_BRANCH_TAG']]
    }
    stage('Another user input') {
        def userInput = input(
            id: 'userInput', message: 'Let\'s promote?', parameters: [
                [$class: 'TextParameterDefinition', defaultValue: 'uat', description: 'Environment', name: 'env'],
                [$class: 'TextParameterDefinition', defaultValue: 'uat1', description: 'Target', name: 'target']
                ])
        echo ("Env: "+userInput['env'])
        echo ("Target: "+userInput['target'])
    }
    stage('Yet another user input') {
        Map feedback = input(submitterParameter: 'submitter', message: "tell me something", parameters: [
            [$class: 'GitParameterDefinition', branch: '', branchFilter: '.*', defaultValue: '', description: 'Git Tag Description', name: 'text', quickFilterEnabled: true, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'PT_BRANCH_TAG']
            ])
        echo "Text: ${feedback.text}"
        echo "Submitter: ${feedback.submitter}"
    }
    stage('Build') {
        echo 'building'
    }

    stage('Test') {
        echo 'testing'
    }

    stage('Deploy') {
        echo 'deploying'
    }
}