pipeline{
    agent any
    tools {
        maven 'Maven' 
    }

    stages{
        stage("project-maven-test"){
            steps{
                sh  ' mvn package  '
                sh  ' docker --version '
            }
        }
        stage("docker build image"){
            steps{
                script {
                sh  ' docker build -t lakshit45/appp . '
                }
            }
        }
        stage("docker build "){
            steps{
                script {
                    withCredentials([string(credentialsId: '', variable: 'password')]) {
  
}
                sh  ' docker login -u lakshit45 -p ${password }'
                sh  ' docker push lakshit45/appp '  
                }
            }
        }
           
    }

    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}
