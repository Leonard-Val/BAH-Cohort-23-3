pipeline{
    environment{
        REGISTRY = "079904783278.dkr.ecr.us-east-1.amazonaws.com/23-3-bah-cohort"
        BUILD_TAG = "1.0.${env.BUILD_NUMBER}"
        REMOTE_DOCKER_HOST = ""
        REMOTE_CONTAINER_NAME = ""
        REMOTE_CONTAINER_PORTS = ""
        REMOTE_CONTAINER_IMAGE_NAME = ""
        SSH_USER = ""
    }
    agent any
    stages{
            stage('Build Webpage'){
                
                steps{
                    sh 'mvn -f Web/hohtrainingapp/pom.xml clean package'
                    sh "cp Web/hohtrainingapp/target/hohtrainingapp.war Docker/hohtrainingapp.war"
                    script{
                        
                    
                        docker.build("${REGISTRY}:${BUILD_TAG}", "Docker --no-cache ")
                        
                        }
                }
                post{
                    success{
                        echo "Archiving Package..."
                        echo 'Docker Build to container'
                         
                        echo 'Tag Entry with ECR'

                        sh (script:"/bin/bash -c 'aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin ${REGISTRY}:${BUILD_TAG}'")
                        archiveArtifacts artifacts: '**/*.war'
                    }
                }
            }
        
            stage('Stage Container in ECR'){
                    steps{
                        
                        echo 'Docker Push to ECR'

                        sh "docker push ${REGISTRY}:${BUILD_TAG}"
                    }
                
            }

            
                        }
                    }
                
            
    
        
            
    




