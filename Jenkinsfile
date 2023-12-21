pipeline {
	agent {
		label {
				label "built-in"
				customWorkspace "/mnt/workspace/23q1"
		}
	}
	stages {
		stage ("clone code") {
			steps {
				git branch: '23q1', url: 'https://github.com/shreeyashswami/navinrepo.git'	
			}
		}
		stage ("crate container") {
			steps {
					sh "docker kill container_one"
					sh "docker rm container_one"
					sh "docker run --name container_one -itdp 80:80 httpd"
			}
		}
		stage ("deploy") {
			steps {
					sh "chmod -R 777 index.html"
					sh "docker cp index.html container_one:/usr/local/apache2/htdocs"
			}
		}
	}
}
