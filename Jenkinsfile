pipeline {
    agent { label 'agente1' }
    stages {
        stage('download') {
            steps {
                sh '''
                ls
                echo "hola"
                echo $prueba
                pwd
                ls -lrt
                echo $password
                pwd
                uname
                docker ps
                hostname
                touch 1
                '''
            }
        }
        stage('compilar') {
            steps {
                sh '''
                cd /home/devops/sparkjava-war-example/
                docker run -it --rm --name my-maven-project -v "$(pwd)":/usr/src/mymaven -w /usr/src/mymaven maven:3.3-jdk-8 mvn clean install
                '''
            }
        }
        stage('deployar') {
            steps {
                sh '''
                docker cp /home/devops/sparkjava-war-example/target/sparkjava-hello-world-1.0.war tomcat://usr/local/tomcat/webapps
                
                '''
            }
        }
    }
}
