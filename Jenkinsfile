// pipeline {
//     agent {
//         docker {
//             image 'maven:3-alpine'
//             args '-v /root/.m2:/root/.m2'
//         }
//     }
//     stages {
//         stage('Build') {
//             steps {
//                 sh 'mvn -B -DskipTests clean package'
//             }
//         }
//         stage('Test') {
//             steps {
//                 sh 'mvn test'
//             }
//             post {
//                 always {
//                     junit 'target/surefire-reports/*.xml'
//                 }
//             }
//         }
//         // stage('Deliver') {
//         //     steps {
//         //         sh './jenkins/scripts/deliver.sh'
//         //     }
//         // }
//     }
// }

node{
    withDockerContainer(args: '-v /root/.m2:/root/.m2', image: 'maven:3-alpine'){
     stage('Build'){
         sh 'mvn -B -DskipTests clean package'
    }
    stage('Test'){
        sh 'mvn test'
        junit 'target/surefire-reports/*.xml'
    }
    }
   
}
