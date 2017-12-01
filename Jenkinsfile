#!groovy
node("392641ad9392-3acb3aef") {
    def toUpdate = new HashMap()
    def listOfComponents = ["componentA"]
    def brachName = "integration%2FJIRA-1234"
    stage("run downstream job") {
        //listOfComponents.each {
            build job: "componentA/${brachName}", parameters: [[$class: 'StringParameterValue', name: 'componentsToUpdate', value: "componentA"]]
        //}
    }
}