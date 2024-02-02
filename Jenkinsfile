pipeline {
    agent any

    stages {
        stage('Clonando Repositório Git') {
            steps {
                git branch: 'main', url: 'https://github.com/leandrolimae91/jk-public-gh.git'
            }
        }
        
        stage('Construindo Imagem') {
            steps {
                sh 'docker build -t webapp:${BUILD_NUMBER} .'   
            }
        }
        
        stage('Deploy') {
            steps {
                sh ''' 
                # docker stop webapp_ctr
                docker run --rm -d -p 3000:3000 --name webapp_ctr webapp:${BUILD_NUMBER}  
            '''    
            }
        }
    }                                       
}
