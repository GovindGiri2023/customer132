pipeline {
    agent any
          stages {
              stage('New port number') {
                    steps {
                          withCredentials([
                          usernamePassword(
                          credentialsId: "	Git_hub_id",
                          passwordVariable: 'PASSWORD',
                          usernameVariable: 'USER'
                           )   ]) 
                        {
                          sh 'sudo sh gitbranch.sh $USER $PASSWORD $NAME '
                          sh "echo $USER"
                        }
                  }  
              }
              stage('Creating new Branch') {
                   steps {
                      withCredentials([gitUsernamePassword(credentialsId: 'Git_hub_id', gitToolName: 'git-tool')]) {
                          sh 'll'
                     }
                   }
              }
              stage('Creating GIt Repo') {
                  steps {
                      
                      sh 'sudo sh gitbranch.sh $USER_NAME $GIT_TOKEN $REPO_NAME '
                  }
              }  
         
              stage('Change namespaces') {
                  steps {
                      
                      sh 'sudo sh namespace.sh $NAME $DOMAIN $PORTNUMBER'
                  }
              }  
              stage('New port number') {
                  steps {
                      
                      sh 'sudo sh SG_Update.sh $PORTNUMBER'
                  }
              }   
           }
    
}
