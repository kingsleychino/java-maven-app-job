def gv

pipeline {
    agent any

    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: 'Select the version to build')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Check to run tests')
    }

    stages {
        stage("init") {
            steps {
                script {
                    // This loads the external groovy file into the gv variable
                    gv = load "script.groovy"
                }
            }
        }
        
        stage("build") {
            steps {
                script {
                    // Calls the buildApp function from script.groovy
                    gv.buildApp()
                }
            }
        }
        
        stage("test") {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                script {
                    gv.testApp()
                }
            }
        }
        
        stage("deploy") {
            steps {
                script {
                    gv.deployApp()
                }
            }
        }
    }
}
