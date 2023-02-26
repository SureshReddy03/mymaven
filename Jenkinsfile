pipeline
{
    agent any
    stages
    {
        stage('continousdownload')
        {
            steps
            {
               script
               {

                  try
                  {
                    git '  https://github.com/SureshReddy03/mymaven.git'
                  }
                  catch(Exception e1)
                  {
                     mail bcc: '', body: 'jenkins is unable to download the remote from git repo', cc: '', from: '', replyTo: '', subject: 'Git failed', to: 'git.admin@gmail.com'
                     exit(1)
                  }
               
               }
           }  
        }
        stage('continousbuild')
        {
            steps
            {
             
               script
               {
                
                 try
                 {
                    sh 'mvn package'
                 }
                 catch(Exception e2)
                 {
                    mail bcc: '', body: 'jenkins is unable to download the remote from git repo', cc: '', from: '', replyTo: '', subject: 'Git failed', to: 'git.admin@gmail.com'
                     exit(2) 
                 }
  
               }
            }
        }
        stage('continousdeploy')
        {
            steps
            {
             
               script
               {
    
                  try
                  {
                     deploy adapters: [tomcat9(credentialsId: '7217269f-3bf0-46b6-a7b6-9fd7f67d22ae', path: '', url: 'http://172.31.31.4:8080')], contextPath: 'qaserver', war: '**/*.war'
                  }
                  catch(Exception e3)
                  {
                     mail bcc: '', body: 'jenkins is unable to download the remote from git repo', cc: '', from: '', replyTo: '', subject: 'Git failed', to: 'git.admin@gmail.com'
                     exit(3)
                  }         

               }
            }
        }
        stage('continoustesting')
        {
            steps
            {
                  
                script
                {

                    try
                    {
                      git 'https://github.com/SureshReddy03/Testing.git'

                      sh 'java -jar /var/lib/jenkins/workspace/development/testing.jar'
                    }
                    catch(Exception e4)
                    {
                      mail bcc: '', body: 'jenkins is unable to download the remote from git repo', cc: '', from: '', replyTo: '', subject: 'Git failed', to: 'git.admin@gmail.com'
                     exit(4)
                    }
                }
            }
        }
        stage('continousdelivery')
        {
            steps
            {

               script
               {
                 
                   try
                   {
                     deploy adapters: [tomcat9(credentialsId: '7217269f-3bf0-46b6-a7b6-9fd7f67d22ae', path: '', url: 'http://172.31.25.153:8080')], contextPath: 'prodserver', war: '**/*.war'
                   }             
                   catch(Exception e4)
                   {
                      mail bcc: '', body: 'jenkins is unable to download the remote from git repo', cc: '', from: '', replyTo: '', subject: 'Git failed', to: 'git.admin@gmail.com'
                     exit(4)
                   }

               }
            }
        }
   }
}

 
