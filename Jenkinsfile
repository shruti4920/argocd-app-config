pipeline {
    
    agent any
    stages {
        stage("Checkout") {
            steps {
                checkout scm
            }
        }
        
        stage("update git"){
        steps{
        sh "cat .dev/deployment.yaml"
        }
        }
        }
}
