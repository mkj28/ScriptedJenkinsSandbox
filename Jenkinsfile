import groovy.json.JsonSlurperClassic

node {
    checkout scm

    def datasets = jsonParse(readFile("dataset.json"))

    def datasetArrayString = getKeySetAsString(datasets["datasets"])
    println datasetArrayString
    def dataset
    def company
    def phone
    def environment

    stage('Select Dataset') {
        timeout(time: 1, unit: 'HOURS') {
            dataset = input([message: 'Select Dataset', parameters: [[$class: 'ChoiceParameterDefinition', choices: datasetArrayString, description: 'Select Dataset', name: 'dataset']]])
        }
        echo ("Dataset: " + dataset)
    }

    stage('Select company') {
        def companies = datasets["datasets"][dataset]
        def companyString = companies.join("\n")
        timeout(time: 1, unit: 'HOURS') {
            company = input([message: 'Select Company', parameters: [[$class: 'ChoiceParameterDefinition', choices: companyString, description: 'Select Company', name: 'company']]])
        }
        echo ("Company: " + company)
    }

    if( dataset == "travel" ) {
        stage('Phone number') {
            timeout(time: 1, unit: 'HOURS') {
                phone = input([message: 'Phone Number', parameters: [[$class: 'ChoiceParameterDefinition', choices: "1234\n5678", description: 'Phone Number', name: 'phoneNumber']]])
            }
            echo ("Phone: " + phone)
        }

    }

    stage('Select environment') {
        timeout(time: 1, unit: 'HOURS') {
            environment = input([message: 'Select environment', parameters: [[$class: 'ChoiceParameterDefinition', choices: "staging\ndemo", description: 'Environment', name: 'environment']]])
        }
        echo ("Environment: " + environment)
    }

    stage('Reset') {
        echo 'Resetting: ' + environment + " for dataset: " + dataset + " and company: " + company
    }

    stage('Testing') {
        timeout(time: 1, unit: 'HOURS') {
            input message: "Tests passed?"
        }
    }
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