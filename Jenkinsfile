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
                sh  ' docker build -t lakshit45/app . '
                }
            }
        }
        stage("docker build image"){
            steps{
                script {
                sh  ' docker login -u lakshit45 -p jesuschrist@11 '
                sh  ' docker push lakshit45/app '  
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
