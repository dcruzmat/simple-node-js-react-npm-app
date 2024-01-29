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
        stage('OBS bucket setup') {
            steps {
                sh 'curl https://dl.min.io/client/mc/release/linux-amd64/mc --create-dirs -o $HOME/minio-binaries/mc'
		sh 'chmod +x $HOME/minio-binaries/mc'
		sh 'export PATH=$PATH:$HOME/minio-binaries/'
		sh 'mc --help'
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
