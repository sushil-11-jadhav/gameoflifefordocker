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
					sh "service docker start"
					sh "docker kill server"
					sh "docker system prune -a -f"
					sh "docker run -itdp 8081:8080 -v /mnt/gol/gameoflife-web/target:/usr/local/tomcat/webapps --name server tomcat:9.0.74"
			}
		}
		stage ("gol on slave") {
			agent {
				label {
					label "slave"
					customWorkspace "/mnt/gol"
				}
			}
			steps {
					sh "cd /mnt/gol"
					sh "mvn clean install"
					sh "service docker start"
					sh "docker kill server"
					sh "docker system prune -a -f"
					sh "docker run -itdp 8081:8080 -v /mnt/gol/gameoflife-web/target:/usr/local/tomcat/webapps --name server tomcat:9.0.74"
			}
		}
		stage ("gol on slave ssh") {
			agent {
				label {
					label "slave ssh"
					customWorkspace "/mnt/gol"
				}
			}
			steps {
					sh "sudo cd /mnt/gol"
					sh "sudo mvn clean install"
					sh "sudo service docker start"
					sh "docker kill server"
					sh "docker system prune -a -f"
					sh "sudo docker run -itdp 8081:8080 -v /mnt/gol/gameoflife-web/target:/usr/local/tomcat/webapps --name server tomcat:9.0.74"
			}
		}
	}
}
