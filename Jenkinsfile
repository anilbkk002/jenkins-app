node{
      def mvnHome = tool name: 'maven 3.5.4', type: 'maven' 
      stage('Checkout'){
         git 'https://github.com/LovesCloud/java-tomcat-maven-example'
       
      }  
      stage('Build'){
         //// Get maven home path and build
        sh "${mvnHome}/bin/mvn clean package -Dmaven.test.skip=true"
      }
     stage ('Test-JUnit'){
         sh "'${mvnHome}/bin/mvn' test surefire-report:report"
      }  
    
      stage('Deploy') {     
    //       sshagent(['deploy_user']) {
    // some block
    //    sh 'sudo chown -R ubuntu:ubuntu /var'
    //    sh 'sudo chown -R ubuntu:ubuntu /opt'
        sh 'scp -o StrictHostKeyChecking=no target/tomcatdeploymnetdemo.war ubuntu@18.218.216.187:/var/lib/tomcat9/webapps'
    //    sh 'sudo systemctl restart tomcat9' 
          sh echo 'application deployed"    
          }
         
     }
      
 }
