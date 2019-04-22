node ('master'){

    stage ('checkoutSCM')
    
    {
       cleanWs cleanWhenSuccess: false
       checkout([$class: 'GitSCM', 
       branches: [[name: '*/master']],
       doGenerateSubmoduleConfigurations: false, 
       extensions: [], 
       submoduleCfg: [], 
       userRemoteConfigs: [[credentialsId: 'SB237H',
       url: 'https://gitlab.com/admin-2013/My-Project.git']]])
    }
    
    stage('build')
           {
          sh label: '', script: 'mvn package'
         
            archiveArtifacts '**/*.war'
              
           }
          

     stage('Deployment')
           {
sh label: '', script: 'scp /var/lib/jenkins/workspace/Scripted-Pipeline/webapp/target/webapp.war ubuntu@172.31.15.125:/var/lib/tomcat8/webapps/queen.war'
        }           


  stage('Productiont')
  
           {
           
              input id: 'NHBN9', message: 'Waiting for the proceed', ok: 'submit', submitter: 'venkat'
           
sh label: '', script: 'scp /var/lib/jenkins/workspace/Scripted-Pipeline/webapp/target/webapp.war ubuntu@172.31.18.214:/var/lib/tomcat8/webapps/king.war'
        }           



}
