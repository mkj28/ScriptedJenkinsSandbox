node {
    stage('User input') {
        input message: 'Which git tag?', parameters: [[$class: 'GitParameterDefinition', branch: '', branchFilter: '.*', defaultValue: '', description: '', name: 'tes', quickFilterEnabled: false, selectedValue: 'NONE', sortMode: 'NONE', tagFilter: '*', type: 'PT_TAG']]
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