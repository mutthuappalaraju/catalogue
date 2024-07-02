pipeline {
    agent {
        node {
            label 'AGENT-1'
        
        }
    }
    
    environment { 
        packageVersion = ''
    }
    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
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
        stage('Install dependencies') {
            steps {
                sh """
                 npm install
                """
            }
        }
        stage('Build') {
            steps {
                sh """
                  ls -la
                  zip -q -r catalogue.zip  ./* -x ".git" -x "*.zip"
                  ls -ltr
                """
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
             deleteDir()
        }
        failure { 
            echo 'when indicate job failure'
        }
        success { 
            echo 'when job success'
        }
    }
}


