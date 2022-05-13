pipeline{
    agent any
    environment{
        NEW_VERSION='1.4.0'
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
