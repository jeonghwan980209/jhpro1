pipeline {
    agent any
    stages {
        stage('gitlab scm update') {
            steps {
                git url: 'https://github.com/jeonghwan980209/project1.git', branch: 'master'
            }
        }
        stage('이미지 생성') {
            steps {
                sh '''
                docker build -t 211.183.3.115/project/project:jh .
                sudo docker push 211.183.3.115/project/project:jh
                '''
            }
        }
        stage('앤서블로 실행') {
            steps {
                sh '''
                ansible-playbook -i /root/pro1/hosts playbook.yml
                '''
            }
        }
    }
}
