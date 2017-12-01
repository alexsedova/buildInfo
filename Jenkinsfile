#!groovy
node("392641ad9392-3acb3aef") {
    def toUpdate = []
    def listOfComponents = ["componentA", "componentB"]
    def brachName = "integration%2FJIRA-1234"
    stage("run downstream job") {
        def resultOfBuild = null
        for(i in listOfComponents) {
            resultOfBuild = build job: "${i}/${brachName}", parameters: [[$class: 'StringParameterValue', name: 'componentsToUpdate', value: "${i}"]]
            toUpdate.add(resultOfBuild.rawBuild.environment.UPDATED_COMPONENTS)
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