pipeline {
	agent {
		label {
				label "built-in"
				customWorkspace "/mnt/workspace/23q2"
		}
	}
	stages {
		stage ("clone code") {
			steps {
					git branch: '23q2', credentialsId: 'token-key', url: 'https://github.com/Roshanpachpande01/new.git'
			}
		}
		stage ("crate container") {
			steps {
					sh "docker kill container2"
					sh "docker rm container2"
					sh "docker run --name container2 -itdp 90:80 httpd"
			}
		}
		stage ("deploy") {
			steps {
					sh "chmod -R 777 index.html"
					sh "docker cp index.html container2:/usr/local/apache2/htdocs"
			}
		}
	}
}
