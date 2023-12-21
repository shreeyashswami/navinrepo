pipeline {
	agent {
		label {
				label "built-in"
				customWorkspace "/mnt/workspace/23q3"
		}
	}
	stages {
		stage ("clone code") {
			steps {
					git branch: '23q3', url: 'https://github.com/shreeyashswami/navinrepo.git'
			}
		}
		stage ("crate container") {
			steps {
					sh "docker kill container_three"
					sh "docker rm container_three"
					sh "docker run --name container_three -itdp 8080:80 httpd"
			}
		}
		stage ("deploy") {
			steps {
					sh "chmod -R 777 index.html"
					sh "docker cp index.html container_three:/usr/local/apache2/htdocs/"
			}
		}
	}
}
