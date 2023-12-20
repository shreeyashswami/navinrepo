pipeline {
	agent {
		label {
				label "built-in"
				customWorkspace "/mnt/workspace/23q4"
		}
	}
	stages {
		stage ("clone code") {
			steps {
					git branch: '23q4', credentialsId: 'token-key', url: 'https://github.com/Roshanpachpande01/new.git'
			}
		}
		stage ("crate container") {
			steps {
					sh "docker kill container_four"
					sh "docker rm container_four"
					sh "docker run --name container_four -itdp 8001:80 httpd"
			}
		}
		stage ("deploy") {
			steps {
					sh "chmod -R 777 index.html"
					sh "docker cp index.html container_four:/usr/local/apache2/htdocs"
			}
		}
	}
}
