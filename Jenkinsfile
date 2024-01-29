pipeline {
    agent any

    tools {nodejs "nodejs20"}

    stages {
        stage('Build Static Site') {
            steps {
                sh 'npm install'
		sh 'npm run build'
		sh 'ls ./build'
            }
        }
        stage('OBS Bucket Setup') {
            steps {
                sh 'curl https://dl.min.io/client/mc/release/linux-amd64/mc --create-dirs -o $HOME/minio-binaries/mc'
		sh 'chmod +x $HOME/minio-binaries/mc'
		sh '$HOME/minio-binaries/mc alias set myobs https://obs.la-north-2.myhuaweicloud.com VBQOAC5EIGTZ43NGMTQR U0yCk3XtNrBOfrdm34qkqtgaiw7iGyVaZLU36ARx'
		sh '$HOME/minio-binaries/mc alias list'
		sh '$HOME/minio-binaries/mc ls myobs/cra-test'
            }
        }
        stage('Deploy Static Site to OBS') {
            steps {
                sh 'cd ./build'
		sh '$HOME/minio-binaries/mc cp ~/build/. myobs/cra-test/.'
            }
        }
    }
}
