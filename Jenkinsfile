env.mvnHome = '/usr/share/maven'
node('maven-label') {
   
   
   stage('Preparation') { // for display purposes
      
      git 'https://github.com/quickfixtech/myapp.git'
        
      
   }
   stage('Build') {
      
      if (isUnix()) {
         sh "'${mvnHome}/bin/mvn' clean install"
      } else {
         bat(/"${mvnHome}\bin\mvn" -Dmaven.test.failure.ignore clean package/)
      }
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archive 'target/*.jar'
   }
   

}
