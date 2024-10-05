pipeline{
    agent any
    tools{
        maven 'my-maven'
        jdk 'my-jdk'
    }
    stages{
        stage('Clone'){
            steps{
                git url:'https://github.com/gururaj-r123/employee-service.git',branch:'main'
            }
        }
        stage('Build'){
            steps{
                bat "mvn clean install -DskipTests"
            }
        }
        stage('Test'){
            steps{
                bat "mvn test"
            }
        }
        stage('Deploy'){
            steps{
                bat "docker rm -f my-emp-container"
                bat "docker rmi -f my-emp-image"
                bat "docker build -t my-emp-image ."
                bat "docker run -p 8761:8761 -d --name my-emp-container my-emp-image"
            }
        }
    }
}
