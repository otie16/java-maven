pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages {
        stage('Build') {
            steps {
                echo "Building the app"
                // Your build commands here
            }
        }

        stage('Test') {
            steps {
                echo "Running tests..."
                // Your test commands here
            }
        }

        stage('Deploy') {
            steps {
                echo "deploying the app..."
                echo "Deploying version ${params.VERSION}..."
                
                // Your deployment commands here
            }
        }
    }
}