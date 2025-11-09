@Library('Shared') _
pipeline{
    agent { label 'one'}
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code clone"){
            steps{
                script{
                    clone("https://github.com/LondheShubham153/django-notes-app.git","main")
                }    
            }
        }
        stage("Code Build"){
            steps{
                script{
                    docker_build("notes-app","latest","microskills")
                }
            }
        }
        stage("Push to DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","microskills")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "this is deploying the code"
                sh "docker compose up -d"
            }
        }
        
    }
}
