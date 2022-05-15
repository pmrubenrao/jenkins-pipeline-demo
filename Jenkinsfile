def gv
pipeline{
    agent any
    parameters{
//         string(name: 'VERSION', defaultValue:'', desc='description')
        choice(name: 'VERSION',choices:['1.1.0','1.2.0', '1.3.0'], description:' choioces' )
        choice(name:'Deplot-to:',choices["INT","PRE-PROD","PROD"])
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
             parallel{
                    stage("INT") {
                    when { expression { params.DEPLOY_TO == "INT" } }
                    steps {
                        sh "./deploy int"
                    }
                }
                stage("PRE") {
                    when { expression { params.DEPLOY_TO == "PRE" } }
                    steps {
                        sh "./deploy.sh pre"
                    }
                }
                stage("PROD") {
                    when { expression { params.DEPLOY_TO == "PROD" } }
                    steps {
                        sh "./deploy.sh prod"
                    }
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
