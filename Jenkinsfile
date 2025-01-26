@Library("sharedlib") _
pipeline{
    
         agent{label "Nitish"}
         stages{
             stage("hello"){
                 steps{
                     script{
                        hello()
                     }
                  }
            }
             stage("code"){
                 steps{
                       script{
                       clone("https://github.com/Nitish8979/django-notes-app.git","main")
                       }
                 }
            }
             stage("Build"){
                 steps{
                     script{
                     docker_build("notes-app","latest","nitishdevops")
                     }
                 }
            }
             stage("Push to DockerHub"){
                 steps{
                     script{
                         docker_push("notes-app","latest","nitishdevops")
                     }
                
                 }
        
             }
             stage("Deploy"){
                 steps{
                     echo "This is deploying the code"
                     sh "docker-compose down && docker-compose up -d "
            
                 }
              }
        
        
         }
    
    }
