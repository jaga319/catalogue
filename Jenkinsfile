pipeline {
  agent {
    node {
        label 'AGENT-1'
    }
  } 
  options{
        timeout(time: 1,unit:'HOURS')
        disableConcurrentBuilds()
        ansiColor('xterm')
    }
    // Build //
    environment {
        packageversion = ''
    }
    stages {
        stage('get_version') {
            steps {
                script {
                        def PackageJson = readJSON file: 'package.json'
                        packageversion = PackageJson.version
                        echo "application version is ${packageversion}"
                }
            }
        }
        stage ('install dependencies'){
            steps{
                sh """
                 npm install
                """
            }
        }
        stage ('Build'){
            steps{
                sh """
                   ls -la
                   zip -r catalogue.zip ./* -x ".git" -x ".zip"
                   ls -ltr
                """
            }
        }

        
    }
    // post build 
     post { 
        always { 

            echo 'I will always run'
            deleteDir()
        }
        failure{
            echo 'job is failed , creating an alarm'
        }
        success{
            echo 'job completed successfully'
        }
    }
}
