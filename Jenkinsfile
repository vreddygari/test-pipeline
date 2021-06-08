pipeline {

  agent any
  
environment {
    
    ANYPOINT_CREDS = credentials('anypoint_credentials')
   
  }
 
  stages {
    stage('Build') {
      steps {
            bat 'mvn -B -U -e -V clean -DskipTests package'
      }
    }

    stage('Test') {
      steps {
         echo " Munit test case is successfull"
      }
    }

     stage('Deploy Development') {
     
     environment {
    
    client_id = credentials('dev_client_id')
    client_secret = credentials('dev_client_secret')
   
 				 }
     
     
      steps {
            bat 'mvn -U -V -e -B -DskipTests -PDev deploy -DmuleDeploy -Dusername="%ANYPOINT_CREDS_USR%" -Dpassword="%ANYPOINT_CREDS_PSW%" -Dclient_id="%client_id%" -Dclient_secret="%client_secret%" ' 
      }
    }
 
  }

}