node {
	def gradleContainer = docker.image('gradle:jdk8-alpine')
	gradleContainer.pull()
	stage('prep') {
		checkout scm
	}
	stage('test') {
		gradleContainer.inside(" -v ${env.HOME}/.gradle:/home/gradle/.gradle") {
			sh './gradlew test'
		}
	}
	stage('run') {
		gradleContainer.inside(" -v ${env.HOME}/.gradle:/home/gradle/.gradle") {
			sh './gradlew run'
		}
	}
}