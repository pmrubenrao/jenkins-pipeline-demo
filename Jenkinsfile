CODE_CHANGES = getGitChanges()
pipeline{
    agent any
    stages{
        stage("build"){
            when{
               expression {
                    BRANCH_NAME == 'main' || BRANCH_NAME == 'master'
                }
            }
            steps{
                echo " Build Stage"
            }
        }
        stage("test"){
            when {
                expression {
                    BRANCH_NAME == 'main' || BRANCH_NAME == 'master'
                }
            }
            steps{
                echo " test Stage"
            }
        }
        stage("deploy"){
            steps{
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
