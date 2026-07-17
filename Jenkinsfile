@Library("shared") _
pipeline{
    
    agent { label "alex"}
    
    stages{
        stage("Hello") {
            steps{ 
                script {
                    hello()
                }
            }
        }
        
        stage("Code") {
            steps{ 
                script { 
                    clone("https://github.com/nitishkumar-devops/django-notes-app.git", "main")
                }
            }
        }
    
        stage("Build") {
            steps{ 
                script {
                    docker_build("notes-app", "latest", "cloudnitish")
                }
            }
        }
        
        stage("Push to DockerHub") {
            steps{ 
               script{
                   docker_push("notes-app", "latest", "cloudnitish")
                   }
                }
            }

        stage("Deploy") {
            steps{ 
                echo "This is Deploying code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
