pipeline{
    agent any
    tools{
        jdk 'myjava'
        maven 'mymaven'
    }
    environment{
          NEW_VERSION='1.4.0'
    }
    stages{
        stage("COMPILE"){
          
            steps{
                script{
                    echo "Compiling the code"
                    git 'https://github.com/Ravikumar132/addressbook.git'
                    sh 'mvn compile'
                }
            }
        }
        stage("UNITTEST"){
            steps{
                script{
                    echo "Testing the code"
                    sh 'mvn test'
                }
            }
            post{
                always{
                    junit 'target/surefire-reports/*.xml'
                }
            }
        }
         stage("PACKAGE"){
            steps{
                script{
                    echo "Building the app"
                    echo "building version ${NEW_VERSION}"
                    sh 'mvn package'
                }
            }
        }
    }
}
