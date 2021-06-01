pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				bat 'mvn clean install'
			}
		}
		stage('Upload') {
			steps {
			    script {
					if (params.ENVIRONMENT == 'E2E Environment'){
						bat 'curl -u admin:admin -F package=@"ui.apps/target/mysite.ui.apps-1.0.0-SNAPSHOT.zip" http://localhost:4502/crx/packmgr/service/.json/?cmd=upload'
					}
					else{
						bat 'curl -u admin:admin -F package=@"ui.apps/target/mysite.ui.apps-1.0.0-SNAPSHOT.zip" http://localhost:4503/crx/packmgr/service/.json/?cmd=upload'
					}
				}
			}
		} 
	}
}
