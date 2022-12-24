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
        sh "cat ./dev/deployment.yaml"
        echo "${DOCKERTAG}"
        sh "sed-i 's+image-registry.openshift-image-registry.svc:5000/shruti-poc-devops/springboot-app.*+image-registry.openshift-image-registry.svc:5000/shruti-poc-devops/springboot-app:${DOCKERTAG}+g' deployment.yaml"
        sh "cat ./dev/deployment.yaml"
        }
        }
        }
}
