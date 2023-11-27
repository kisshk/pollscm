pipeline
{
    agent any
    stages
    {
        stage('ContineousDownload')
        {
            steps
            {
                git 'https://github.com/kisshk/pollscm.git'
            }
        }
        stage('ContineousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContineousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'ae4f619b-d44c-4da3-b16e-eea31f99e81f', path: '', url: 'http://172.31.42.163:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
        stage('ContineousTesting')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /home/ubuntu/.jenkins/workspace/DeclaritivePipeline/testing.jar'
            }
        }
        stage('ContineousDelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'ae4f619b-d44c-4da3-b16e-eea31f99e81f', path: '', url: 'http://172.31.32.246:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
    }
}
