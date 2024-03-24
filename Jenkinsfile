pipeline
{
    agent any
    stages
    {
        stage('Download')
        {
            steps
            {
                git 'https://github.com/Ak-1920/Maven34.git'
            }

        }
        stage('Build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Deploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'ff45d6f7-f150-4059-8cad-3a79ca310759', path: '', url: 'http://172.31.47.88:8080')], contextPath: 'testapp', onFailure: false, war: '**/*.war'
            }
        }
        stage('Test')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/FirstJob/testing.jar'
            }
        }
        stage('Delivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '72722bd4-d861-4047-82f4-920d377c1345', path: '', url: 'http://172.31.43.203:8080')], contextPath: 'prodapp', onFailure: false, war: '**/*.war'
            }
        }

    }
}
