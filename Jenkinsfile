pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git 'git@github.com:RuMurf/student-driver.git'
            }
        }
        stage("Set Up") {
            steps {
                sh "chmod +x gradlew"
            }
        }
        stage("Compile Code") {
            steps {
                echo "Compiling code"
                sh "./gradlew compileJava"
            }
        }
        stage("Compile Tests") {
            steps {
                echo "Compiling tests"
                sh "./gradlew compileTestJava"
            }
        }
        stage("Test") {
            steps{
                echo "Running tests"
                sh "./gradlew test"
            }
        }
        stage("Build") {
            steps {
                echo "Tests ran successfullly, building project"
                sh "./gradlew build"
            }
        }
        stage('Results') {
            steps {
                archiveArtifacts 'build/libs/*.war'
            }
        }
    }
}
