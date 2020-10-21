node {
	echo 'jenkins file started....'
	def gradleContainer = docker.image('gradle:jdk8-alpine')
	echo 'jenkins file started p1....'
	this.gradleContainer.pull()
	echo 'jenkins file started p2....'
	stage('prep') {
		echo 'prep started....'
		checkout scm
		echo 'prep ended....'
	}
	stage('test') {
		echo 'test started....'
		this.gradleContainer.inside(" -v ${env.HOME}/.gradle:/home/gradle/.gradle") {
			sh './gradlew test'
		}
		echo 'test ended....'
	}
	stage('run') {
		echo 'run started....'
		this.gradleContainer.inside(" -v ${env.HOME}/.gradle:/home/gradle/.gradle") {
			sh './gradlew run'
		}
		echo 'run ended....'
	}
}