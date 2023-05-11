pipeline {
	agent {
		label {
			label "built-in"
			customWorkspace "/mnt/gol"
		}
	}
	stages {
		stage ("stage1") {
			steps {
					sh "cd /mnt/gol"
					sh "mvn clean install"
					sh "docker run -itdp 8081:8080 -v /mnt/gol/gameoflife-web/target:/usr/local/tomcat/webapps --name server tomcat:9.0.74"
			}
		}
	}
}
