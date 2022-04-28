pipeline{
    agent any
    tools {
        maven 'Maven' 
    }

    stages{
        stage("project-maven-test"){
            steps{
                sh  ' mvn test '
            }
        }
            stage("project-maven-build"){
            steps{
               sh 'mvn package'

            }
        }
            stage("project-test-deploy"){
            steps{
               input 'continue?'
               deploy adapters: [tomcat9(credentialsId: 'tomcat9detail', path: '', url: 'http://192.168.1.64:8081/')], contextPath: '/maven', war: '**/*.war'
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
