def gv

pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage('init ') {
            steps{
                script{
                    gv = load "scipt.groovy"
                }
            }

        }
        stage('Build') {
            steps {
                script{
                    gv.buildApp()
                }
                
                }
               
                // Your build commands here
            }
        

        stage('Test') {
            steps {
               script{
                gv.testApp()
               }
                // Your test commands here
            }
        }


        stage('Deploy') {
            steps {
               script{
                gv.deployApp()
               }
               
                
                // Your deployment commands here
            }
        }
    }

}