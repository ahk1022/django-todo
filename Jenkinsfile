@Library("shared") _
pipeline{
    
    agent { label "ahk" }
    
    
    stages{
        
        stage("script"){
            
            steps{
                
                script{
                    
                    hello()
                }
            }
        }
        
        stage("code"){
            
            steps{
                
                echo "code cloning"
                script{
                    clone("https://github.com/ahk1022/django-todo.git","feature/deploy-app")
                }
            }
        }
        stage("build"){
            steps{
                
                echo "code build"
                docker_build("todo-app","latest","ahk3983")
                   
            }
        }
        stage("Pust to DockerHub"){
            
            steps{
                script{
                    
                    docker_push("todo-app","latest","ahk3983")
                }
            }
        }
        stage("deploy"){
            steps{
                
                echo "deploy stage"
                sh "docker compose up"
            }
        }
    }
    
}
