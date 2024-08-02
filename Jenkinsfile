pipeline {
    agent any
    environment {
      WS = "$WORKSPACE"
    }
    //定义流水线的加工流程
    stages {
        stage('stage1.环境检查'){
            steps {
                sh 'printenv'
                sh 'id'
                sh 'docker version'
                sh 'java -version'
                sh 'git --version'
                sh 'mvn -v'
                sh 'pwd && ls -alh'
            }
        }
        stage('stage2.项目编译'){
            steps {
               sh 'mvn clean package -Dmaven.test.skip=true'
            }
        }
        stage('stage3.应用部署'){
            steps {
                sh 'docker-compose -f docker-compose.dev.yml -p fenix up -d'
            }
        }
    }
}