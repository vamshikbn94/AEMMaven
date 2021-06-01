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
			  
				        withCredentials(bindings: [[$class: 'UsernamePasswordMultiBinding', credentialsId: ${BUILD_USER_ID},
                              usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD']]) {
							echo "File already exists within Nexus repository $USERNAME ::$PASSWORD "
							bat 'curl -u $USERNAME:$PASSWORD -F package=@"ui.apps/target/mysite.ui.apps-1.0.0-SNAPSHOT.zip" http://localhost:4502/crx/packmgr/service/.json/?cmd=upload'
						
					}
				
			}
		} 
	}
}
