node {
    checkout scm

    sh "jq datasets.json"
    //datasets = parseText(new File('./dataset.json').text)
    def datasets = readFile "dataset.json"

    

    println datasets
    echo datasets

    stage('Select Dataset') {
        def dataset = input([message: 'Select Dataset', parameters: [[$class: 'ChoiceParameterDefinition', choices: 'retail\nhotel\ncommunication\nfinancial\ntravel', description: 'Select Dataset', name: 'dataset']]])
        echo ("Dataset: "+dataset)
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

def parseText(txt){
        return new groovy.json.JsonSlurper().parseText(txt)
    }