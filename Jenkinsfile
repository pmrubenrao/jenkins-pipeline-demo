def gv
pipeline{
    agent any
    parameters{
//         string(name: 'VERSION', defaultValue:'', desc='description')
        choice(name: 'VERSION',choices:['1.1.0','1.2.0', '1.3.0'], description:' choioces' )
        booleanParam(name:'executeTests', defaultValue:true, description:'boolean')
    }
    environment{
        NEW_VERSION='1.4.0'
        SEVER_CREDENTIALS=credentials('pipeline-cred')
    }
    stages{
        stage("Initialization"){
            steps{
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage("build"){
           steps{
               script {
                    gv.buildApp()
               }               
            }
        }
        stage("test"){
            steps{
               script {
                    gv.testApp()
               }               
            }
        }
        stage("deploy"){
            steps{
               script {
                    gv.deployApp()
               }               
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
