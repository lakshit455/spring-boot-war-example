pipeline{
    agent any

    tools {
        maven 'Maven' 
    }

    stages{
        stage("project-unit-test"){
            steps{
                // mvn test
                sh 'mvn test'
            }
            
        }
        stage("project-build"){
            steps{
                // mvn build
                sh 'mvn package'
            }
            
        }
        stage("project-test-deploy"){
            steps{
                // test deploy 
                deploy adapters: [tomcat9(credentialsId: 'tomcat9detail', path: '', url: 'http://192.168.1.64:8081')], contextPath: '/application', war: '**/*war'
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
