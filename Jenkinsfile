import groovy.json.JsonSlurperClassic

node {
    checkout scm


    //datasets = parseText(new File('./dataset.json').text)
    def datasets = jsonParse(readFile("dataset.json"))

    //def datasetArray =  datasets["datasets"].keySet()
    //println datasetArray
    def datasetArrayString = getKeySetAsString[datasets["datasets"]]
    println datasetArrayString
    def dataset

    stage('Select Dataset') {
        dataset = input([message: 'Select Dataset', parameters: [[$class: 'ChoiceParameterDefinition', choices: datasetArrayString, description: 'Select Dataset', name: 'dataset']]])
        echo ("Dataset: "+dataset)
    }

    stage('Select company') {
        def companies = datasets["datasets"][dataset]
        def companyString = companies.join("\n")
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

@NonCPS
def getKeySetAsString(def json) {
    def keySet = json.keySet()
    return keySet.join("\n")
}