pipeline{
    agent any
    environment{
        NEW_VERSION='1.4.0'
        SEVER_CREDENTIALS=credentials('pipeline-cred')
    }
    stages{
        stage("build"){
            when{
               expression {
                    env.BRANCH_NAME == 'main' || env.BRANCH_NAME == 'master'
                }
            }
            steps{
                echo " Build Stage"
                echo " Building version ${NEW_VERSION}"
            }
        }
        stage("test"){
            when {
                expression {
                    env.BRANCH_NAME == 'main' || env.BRANCH_NAME == 'master'
                }
            }
            steps{
                echo " test Stage"
            }
        }
        stage("deploy"){
            steps{
                echo " Branch name ${env.BRANCH_NAME}"
                withCredentials([usernamePassword(credentialsId: 'pipeline-cred', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {

  sh 'echo $PASSWORD'
  // also available as a Groovy variable
  echo USERNAME
  // or inside double quotes for string interpolation
  echo "username is $USERNAME"
}
               
               echo " Deploy Stage"
            }
        }
        
    }
    post{
        always{
            echo "run always"
        }
        success{
            echo "run on sucess"
        }
        failure{
            echo "run on failure"
        }
    }
}
