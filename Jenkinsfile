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
