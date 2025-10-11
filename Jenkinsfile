node('built-in')
{
    stage('continuous download') 
    {
    git 'https://github.com/IntelliqDevops/maven.git'
}
    stage('continuous build') 
    {
    sh 'mvn package'
      }
    stage('continuous deployment')
   {
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '47cf79da-671b-4f51-969b-c0bd0a80cc30', path: '', url: 'http://172.31.22.182:8080')], contextPath: 'test2', war: '**/*.war'
    }
    stage('continuous Testing')
    {
        git 'https://github.com/IntelliqDevops/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/scripted-pipeline2/testing.jar'
    }
    stage('continuous Delivery')
    {
        deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: '47cf79da-671b-4f51-969b-c0bd0a80cc30', path: '', url: 'http://172.31.21.167:8080')], contextPath: 'prod2', war: '**/*.war'
    }
}
