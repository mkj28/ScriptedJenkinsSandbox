import groovy.json.JsonSlurperClassic

node {
    checkout scm


    //datasets = parseText(new File('./dataset.json').text)
    def datasets = jsonParse(readFile("dataset.json"))

    //def datasetArray =  datasets["datasets"].keySet()
    //println datasetArray
    def datasetArrayString = getKeySetAsString(datasets["datasets"])
    println datasetArrayString
    def dataset
    def company
    def phone
    def environment

    stage('Select Dataset') {
        dataset = input([message: 'Select Dataset', parameters: [[$class: 'ChoiceParameterDefinition', choices: datasetArrayString, description: 'Select Dataset', name: 'dataset']]])
        echo ("Dataset: " + dataset)
    }

    stage('Select company') {
        def companies = datasets["datasets"][dataset]
        def companyString = companies.join("\n")
        company = input([message: 'Select Company', parameters: [[$class: 'ChoiceParameterDefinition', choices: companyString, description: 'Select Company', name: 'company']]])
        echo ("Company: " + company)
    }

    if( dataset == "travel" ) {
        stage('Phone number') {
            phone = input([message: 'Phone Number', parameters: [[$class: 'ChoiceParameterDefinition', choices: "1234\n5678", description: 'Phone Number', name: 'phoneNumber']]])
            echo ("Phone: " + phone)
        }

    }

    stage('Select environment') {
        phone = input([message: 'Select environment', parameters: [[$class: 'ChoiceParameterDefinition', choices: "staging\ndemo", description: 'Environment', name: 'environment']]])
            echo ("Environment: " + environment)
    }

    

    stage('Testing') {
        input message: "Tests passed?"
    }

    stage('Reset') {
        echo 'Resetting: ' + environment + " for dataset: " + dataset + " and company: " + company
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