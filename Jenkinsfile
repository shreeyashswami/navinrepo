pipeline
	agent {
		label {
				label "built-in"
				customWorkspace "/mnt/workspace/23q3"
		}
	}
	stages {
		stage ("clone code") {
			steps {
					git branch: '23q3', credentialsId: 'token-key', url: 'https://github.com/Roshanpachpande01/new.git'
			}
		}
		stage ("crate container") {
			steps {
					sh "docker kill container_three"
					sh "docker rm container_three"
					sh "docker run --name conatiner_three -itdp 8080:80 httpd"
			}
		}
		stage ("deploy") {
			steps {
					sh "chmod -R 777 index.html"
					sh "docker cp index.html container_three:/usr/local/apache2/htdocs"
			}
		}
	}
}
