node('master') 
{
    stage('continuousdownload')
    {
        git 'https://github.com/rajendra538/newwork.git'
    }
    stage('continuousbuild')
    {
        sh 'mvn package'
    }
    stage('continuousdeployment')
    {
     sh ' scp /home/ubuntu/.jenkins/workspace/"scripted pipeline"/webapp/target/webapp.war ubuntu@172.31.59.244:/var/lib/tomcat9/webapps/test.war'
    }
    stage('continuoustesting')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /home/ubuntu/.jenkins/workspace/"scripted pipeline"/testing.jar'
    stage('continuousdelivery')
    {
        input message: 'waiting for the approval from DM!', submitter: 'anusha'
      sh ' scp /home/ubuntu/.jenkins/workspace/"scripted pipeline"/webapp/target/webapp.war ubuntu@172.31.53.146:/var/lib/tomcat9/webapps/prod1.war'
    }
        
        
    }
}
