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
					sh "docker kill container_two"
					sh "docker rm container_two"
					sh "docker run --name container_two -itdp 90:80 httpd"
			}
		}
		stage ("deploy") {
			steps {
					sh "chmod -R 777 index.html"
					sh "docker cp index.html container_two:/usr/local/apache2/htdocs"
			}
		}
	}
}
