pipeline {
    agent {
        environment{
            choice(name: "VERSION", choices: ["1.1.0", "1.2.0", "1.3.0"], description: '')
            booleanParam(name: "executeTests", defaultValue: true, desctiption: "")
        }

        stages {
            stage("Build"){
                steps {
                    echo "Building the applicaiton"
                }
            }

            stage("Test"){
                steps {
                    when {
                        expression {
                            params.executeTests
                            BRANCH_NAME == "main" // Will execute the code only when the current branch is "main"
                        }
                    }

                    echo "Testing the application"
                }
            }

            stage("Deploy"){
                steps {
                    echo "Deploying the application"
                }
            }
        }

        post {
            always {
                junit "test-result/junit.xml"
            }

            success {
                echo "Test: Succeeded"
            }

            failure {
                echo "Test: Failed"
            }
        }
    }
}