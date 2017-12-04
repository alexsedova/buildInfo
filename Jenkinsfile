#!groovy
node("master") {
    def toUpdate = []
    def listOfComponents = ["componentA", "componentB"]
    def brachName = "integration%2FJIRA-1234"
    def item = null
    stage("run downstream job") {
        def resultOfBuild = null
        for(i in listOfComponents) {
            resultOfBuild = build job: "${i}/${brachName}", parameters: [[$class: 'StringParameterValue', name: 'componentsToUpdate', value: "${i}"]]
            println "Is result.env null: " + resultOfBuild.buildVariables
            item = resultOfBuild.buildVariables.UPDATED_COMPONENTS
            println "Item: " + item
            sh "env"
            toUpdate.add(item)
            println "toUpdate: " + toUpdate

        }
        //def stepName = "Run job"
        //componentMap[stepName] = runSeveralJobs(listOfComponents, brachName)
        //parallel componentMap
    }
    stage("Print out toUpdates") {
        println "all: " + toUpdate.toString()
        for(i in toUpdate) {
            println "Current component: " + i
        }
    }
}