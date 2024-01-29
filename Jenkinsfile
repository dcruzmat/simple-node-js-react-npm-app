pipeline {
    agent any

    tools {nodejs "nodejs20"}

    stages {
        stage('Build') {
            steps {
                sh 'npm install'
		sh 'npm run build'
		sh 'ls ./build'
            }
        }
        stage('Deploy') {
            steps {
                sh 'ls ./build'
		sh 'ec alias list'
            }
        }
    }
}
