pipeline{
    agent any
    toold {
        maven 'Maven'
    }
    stages{
        stage("maven test"){
            steps{
                sh 'mvn test'
            }
           
            }
            stage("maven build"){
            steps{
                sh 'mvn  package'
            }
           
            }
            stage("maven deploy"){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'crentials', path: '', url: 'http://192.168.1.64:8081')], contextPath: '/mvnserver', war: '**/*war'
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
