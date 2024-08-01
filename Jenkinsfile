pipeline {
    agent any

    stages {
        stage('Etapa 01: "Clonando Repositório Git') {
            steps {
                git branch: 'main', url: 'https://github.com/rodrigo-bam/jk-public-gh.git'
            }
        }
        stage('Etapa 02: "Construindo Imagem"') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'
            }
        }
        stage('Etapa 03: "Implantando Aplicação"') {
            steps {
                sh '''
                # docker stop webapp_crt
                docker run --rm -d -p 3000:3000 --name webapp_crt webapp:${BUILD_NUMBER}
                '''
            }          
        }
    }
}
