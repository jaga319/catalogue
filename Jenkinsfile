#!groovy
@Library('roboshop-shared-library') _

def configMap = [
    application: 'nodejsvm',
    component: 'catalogue'
]
if ( ! env.BRANCH_NAME.equalsIgnoreCase('main')){
    pipelinedecision.decidePipeline(configMap)
}
else{
    echo "This is production deal with CR process"
}