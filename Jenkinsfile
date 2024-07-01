pipeline {
    agent {
        node {
            label 'AGENT-1'
        
        }
    }
    
    environment { 
        packageVersion = ''
    }

    stages {
        stage ('Get the version') {
            steps {
                script {
                    def packageJson = readJSON file: 'package.json'
                    packageVersion = packageJson.version
                    echo "application version: $packageVersion"
                }
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        // stage('Deploy') {
        //     steps {
        //         sh """
        //            echo 'heloo shell script'
        //            env
        //            echo '$GREETING'
        //         """   
                
        //     }
        // }
         
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
        failure { 
            echo 'when indicate job failure'
        }
        success { 
            echo 'when job success'
        }
    }
}


