properties([buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '', daysToKeepStr: '7', numToKeepStr: '50')), parameters([[$class: 'GitParameterDefinition', branch: '', branchFilter: '.*', defaultValue: '', description: 'Git Branch Or Tag', name: 'GITBRANCHORTAG', quickFilterEnabled: false, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'PT_BRANCH_TAG']]), pipelineTriggers([pollSCM('H/2 * * * *')])])

node {
    stage('User input') {
        input message: 'Select tag', parameters: [[$class: 'GitParameterDefinition', branch: '', branchFilter: '.*', defaultValue: '', description: 'Git Tag Description', name: 'gitTag', quickFilterEnabled: true, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'PT_BRANCH_TAG']]
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