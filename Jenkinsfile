pipeline { 
		agent {
			node {
			label ('built-in')
				}
			}
		stages {
	
		stage ('clone-GOL') {
		steps {
		dir ('/mnt/GOL') {
			sh "rm -rf /root/.m2"
			sh "rm -rf *"
			sh "git clone https://github.com/ronitunale/game-of-life.git"
			sh "chmod -R 777 /mnt/GOL/game-of-life/"
		}
		}
		}
		
			stage ('mvn-install') {
				steps {	
					dir ('/mnt/GOL/game-of-life') {
					sh "mvn install"	
						
					}
				}
			}
		stage ('copy-war-GOL') {
		steps {
			dir ('/mnt/GOL/game-of-life') {
			
			sh "rm -rf *"
			sh "cp gameoflife.war /mnt/server/apache-tomcat-9.0.67/webapps/"
			
			}
			}
			}
			
		stage ('restart-tomcat') {
		steps {
		dir ('/mnt/server/apache-tomcat-9.0.67/bin') {
			sh "./shutdown.sh"
			sh "./startup.sh"

			}
		}
	}
	
	}
}
