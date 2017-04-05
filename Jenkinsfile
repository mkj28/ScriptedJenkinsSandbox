import groovy.json.JsonSlurperClassic

node {
    checkout scm


    //datasets = parseText(new File('./dataset.json').text)
    def datasets = jsonParse(readFile("dataset.json"))

    echo datasets['datasets']'

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

@NonCPS
def jsonParse(def json) {
    new groovy.json.JsonSlurperClassic().parseText(json)
}