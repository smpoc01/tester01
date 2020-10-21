node {
	echo 'jenkins file started....'
	def gradleContainer = docker.image('gradle:jdk8-alpine')
	gradleContainer.pull()
	stage('prep') {
		echo 'prep started....'
		checkout scm
		echo 'prep ended....'
	}
	stage('test') {
		echo 'test started....'
		gradleContainer.inside(" -v ${env.HOME}/.gradle:/home/gradle/.gradle") {
			sh './gradlew test'
		}
		echo 'test ended....'
	}
	stage('run') {
		echo 'run started....'
		gradleContainer.inside(" -v ${env.HOME}/.gradle:/home/gradle/.gradle") {
			sh './gradlew run'
		}
		echo 'run ended....'
	}
}