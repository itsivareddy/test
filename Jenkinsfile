pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/selenium-saikrishna/maven.git'
            }
        }
        stage('ContinuousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('continuos deploy')
        {
            steps
            {
                sh 'scp /var/lib/jenkins/workspace/pipeline/webapp/target/webapp.war /var/lib/tomcat7/webapps/hello2.war'
            }
        }
    }
    post
    {
        success
        {
             input message: 'Waiting for approval', submitter: 'samba'
        sh 'scp /var/lib/jenkins/workspace/pipeline/webapp/target/webapp.war /var/lib/tomcat7/webapps/prodenv1.war'
        }
        failure
        {
            mail bcc: '', body: 'Testing has failed', cc: '', from: '', replyTo: '', subject: '', to: 'dondeti27@gmail.com'   
        }
    }
}
