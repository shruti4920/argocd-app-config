pipeline {
    
    agent any
    stages {
        stage("Checkout") {
            steps {
            //checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'github',url: 'https://github.com/shruti4920/argocd-app-config.git']]])
               checkout scm
        }
            
            
    }
        
        stage("update git"){
        steps{
            withCredentials([usernamePassword(credentialsId: 'github', passwordVariable: 'pass', usernameVariable: 'user')]) {
    // some block

        sh "git config user.email shruti_chittora@persistent.com"
        sh "git config user.name Shruti"
        sh "cat ./dev/deployment.yaml"
        echo "${DOCKERTAG}"
        sh "sed -i 's+image-registry.openshift-image-registry.svc:5000/shruti-poc-devops/springboot-app.*+image-registry.openshift-image-registry.svc:5000/shruti-poc-devops/springboot-app:${DOCKERTAG}+g' ./dev/deployment.yaml"
        sh "cat ./dev/deployment.yaml"
        sh "git add ."
        sh "git commit -m 'done by jenkins job updatemanifest' "
        sh  'git push https://$user:$pass@github.com/$user/argocd-app-config.git HEAD:main'
            }
        }
        }
        }
}
