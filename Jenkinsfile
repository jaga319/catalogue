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
    parameters {
                booleanParam(name: 'deploy', defaultValue: false, description: 'confirm to deploy ?')

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
