pipeline {
    agent any
    tools{
        maven 'maven-3.9'
    }
    stages {
        stage('build jar'){
            steps {
                script{
                    echo "building the application..."
                    sh 'mvn package'
                }
            }
        }
        stage('build image'){
            steps {
                script {
                    echo "building the docker image..."
                    // Extracting the github credentials from jenkins 
                    withCredentials([usernamePassword(credentialsId: 'dockerhub-repo-credentials', passwordVariable: 'PASS', usernameVariable: 'USER', )]){
                        sh 'docker build -t otobongedoho18361/demo-app:jma-2.0 .'
                        sh 'echo $PASS | docker login -u $USER --password-stdin'
                        sh 'docker push otobongedoho18361/demo-app:jma-2.0'
                    } 
                }
            }
        }
    
        stage('deploy'){
            steps {
                script{
                    echo "deploying the application..."
                }
            }
        }
    }
}

// def gv

// pipeline {
//     agent any
//     parameters {
//         choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
//         booleanParam(name: 'executeTests', defaultValue: true, description: '')
//     }
//     stages {
//         stage('init ') {
//             steps{
//                 script{
//                     gv = load "script.groovy"
//                 }
//             }

//         }
//         stage('Build') {
//             steps {
//                 script{
//                     gv.buildApp()
//                 }
                
//                 }
               
//                 // Your build commands here
//             }
        

//         stage('Test') {
//             steps {
//                script{
//                 gv.testApp()
//                }
//                 // Your test commands here
//             }
//         }


//         stage('Deploy') {
//             // input{
//             //     message "select the environment to deploy to"
//             //     ok "Done"
//             //     parameters {
//             //         choice(name: 'ONE', choices:['dev', 'staging', 'prod'], description: 'Environment')
//             //           choice(name: 'TWO', choices:['dev', 'staging', 'prod'], description: 'Environment')
//             //     }    

//             // }
//             steps {
//                script{
//                env.ENV = input message: "Select the environment to deploy to" , ok "Done" , parameters: [choice(name: 'ONE', choices:['dev', 'staging', 'prod'],
//                  description: 'Environment')]
//                 gv.deployApp()
//                 echo "Deploying to ${ENV}"
//                }     
//             }
//         }
//     }
// }
