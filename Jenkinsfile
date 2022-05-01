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
                deploy adapters: [tomcat9(credentialsId: 'tomcat9detail', path: '', url: 'http://192.168.1.64:8081')], contextPath: '/appserver', war: '**/*.war'
                
            }
            
            }
            stage("building docker image"){
            steps{
                
                script{
                sh   ' docker login -u lakshit45 -p jesuschrist@11 '
                sh   'docker build -t lakshit45/img . '

                }
                 
            }
            
            }
            
            stage("building  image"){
            steps{
                
                script{
                  
                sh   'docker push  lakshit45/img '

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
