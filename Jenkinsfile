pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage('init') {  // Corrected space here
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage('Build') {
            steps {
                script {
                    gv.buildApp()
                }
                // Your build commands here
            }
        }
        stage('Test') {
            steps {
                script {
                    gv.testApp()
                }
                // Your test commands here
            }
        }
        stage('Deploy') {
            steps {
                script {
                    env.ENV = input message: "Select the environment to deploy to", ok: "Done", parameters: [
                        choice(name: 'ONE', choices: ['dev', 'staging', 'prod'], description: 'Environment')
                    ]
                    gv.deployApp()
                    echo "Deploying to ${env.ENV}"  // Use env.ENV here
                }
            }
        }
    }
}
