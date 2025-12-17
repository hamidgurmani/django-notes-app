@Library("shared") _
pipeline{
    agent{label "vinod"}
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                 clone("https://github.com/hamidgurmani/django-notes-app.git","main") 
                 
                }
            }
        }
        stage("Build"){
            steps{
                script{
                    docker_build("notes-app", "latest","hamid009")
                }
            }
        }
        stage("Push"){
            steps{
                script{
                    docker_push("notes-app", "latest","hamid009")
                }
                
                echo "pushing end"
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                sh "docker-compose down && docker compose up -d"
            }
        }
    }
}
