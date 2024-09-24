pipeline {
    agent any
    // environment {
    //     NEW_VERSION = '1.3.0'
    //     // SERVER_CREDENTIALS = credentials('server-credentials')
    // }
    // tools{
    //     maven "maven-3.9"
    // }
    parameters {
        // string(name: 'VERSION', defaultValue: '', description: 'Version to be deployed to prod')
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages{
        stage("build") {
            steps {
                echo 'building the application...'
                echo "building version ${NEW_VERSION}"
            }
         }
        stage("test") {
            when {
                expression {
                    params.executeTests == True
                }
            }
            steps {
                  echo 'testing the application...'
            }
        }
        stage("deploy") {
            steps {
                  echo 'deploying the application...'
                  echo "deploying version ${params.VERSION}"
                //   sh "${SERVER_CREDENTIALS}"
                }
            }
        }
    }
