pipeline {
    agent any

    stages {
        stage('Build HelloWorld') {
            steps {
                echo "Compiling and running HelloWorld.java"
                bat '''
                    javac HelloWorld.java
                    java HelloWorld
                '''
            }
        }

        stage('Build HelloWipro') {
            steps {
                echo "Compiling and running HelloWipro.java"
                bat '''
                    javac HelloWipro.java
                    java HelloWipro
                '''
            }
        }

        stage('Build HelloJenkins') {
            steps {
                echo "Compiling and running HelloJenkins.java"
                bat '''
                    javac HelloJenkins.java
                    java HelloJenkins
                '''
            }
        }
    }

    post {
        success {
            echo "✅ All Java programs executed successfully!"
        }
        failure {
            echo "❌ One or more stages failed."
        }
    }
}
