pipeline {

agent any

stages {

  stage('Upload') {

     steps {
       
       sh """mvn clean install"""

        sh """curl -u admin:admin -F package=@"ui.apps/target/mysite.ui.apps-1.0.0-SNAPSHOT.zip" http://localhost:4502/crx/packmgr/service/.json/?cmd=upload"""

     }
  }
} }
