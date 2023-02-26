pipeline
{
    agent any
    stages
    {
        stage('continousdownload')
        {
            steps
            {
             git '  https://github.com/SureshReddy03/mymaven.git'
            }
        }
        stage('continousbuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continousdeploy')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '7217269f-3bf0-46b6-a7b6-9fd7f67d22ae', path: '', url: 'http://172.31.31.4:8080')], contextPath: 'qaserver', war: '**/*.war'
            }
        }
        stage('continoustesting')
        {
            steps
            {
                 git 'https://github.com/SureshReddy03/Testing.git'
                  
                 sh 'java -jar /var/lib/jenkins/workspace/development/testing.jar'
            }
        }
        stage('continousdelivery')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '7217269f-3bf0-46b6-a7b6-9fd7f67d22ae', path: '', url: 'http://172.31.25.153:8080')], contextPath: 'prodserver', war: '**/*.war'
            }
        }
   }
}   
