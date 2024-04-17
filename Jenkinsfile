pipeline {
    agent any{
         label 'test' // Specify the label assigned to your new node
    }
    environment {
        DOCKER_REGISTRY = "gcr.io"  // Your GCR registry URL
        IMAGE_NAME = "frontend" // Your Docker image name
        IMAGE2_NAME = "backend"
        IMAGE3_NAME = "mysql"
        TAG = "latest"  // Tag for your Docker image
        GCP_PROJECT_ID = "jagriti-411012"  // Your GCP project ID
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', credentialsId: '1', url: 'https://github.com/JagritiDubey123/employee-management-jenkins.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    // Build Docker images
                    sh "docker build -f FrontEnd/Dockerfile -t $IMAGE_NAME:$TAG ."
                    sh "docker build -f backend/Dockerfile -t $IMAGE2_NAME:$TAG ."
                    sh "docker build -f mysql/Dockerfile -t $IMAGE3_NAME:$TAG ."
                }
            }
        }

        stage('Run Containers') {
            steps {
                script {
                    // Run MySQL container
                    sh "docker run -d --name mysql -p 3306:3306 $IMAGE3_NAME:$TAG"

                    // Run backend container
                    sh "docker run -d --name backend -p 8000:8000 --link mysql:mysql $IMAGE2_NAME:$TAG"

                    // Run frontend container
                    sh "docker run -d --name frontend-container --link mysql:mysql -p 5000:5000 $IMAGE_NAME:$TAG"
                }
            }
        }
    }
}

// pipeline {
//     agent any
//    environment {
//         DOCKER_REGISTRY = "gcr.io"  // Your GCR registry URL
//         IMAGE_NAME = "frontend" // Your Docker image name
//         image2 = "backend"
//         image3 = "mysql"
//         TAG = "latest"  // Tag for your Docker image
//         GCP_PROJECT_ID = "jagriti-411012"  // Your GCP project ID
//         // GCP_SERVICE_ACCOUNT_KEY = credentials('GCP_ID')  // Jenkins credentials for GCP service account key file
//     }

//     stages {
//         stage('Checkout') {
//             steps {
//                 git branch: 'main', credentialsId: '1', url: 'https://github.com/JagritiDubey123/employee-management-jenkins.git'
//             }
//         }
    
   
//         stage('Build Docker Image') {
//             steps {
//                 script {
//                     // Build Docker image
//                     sh "docker build -f FrontEnd/Dockerfile ."
//                     sh "docker build -f backend/Dockerfile ."
//                     sh "docker build -f mysql/Dockerfile ."
//                 }
//             }
//         }
//       stage('Run Containers') {
//             steps {
//                 script {
//                     // Run MySQL container
//                     sh "docker run -d --name mysql -p 3306:3306 mysql-image"

//                     // Run backend container
//                     sh "docker run -d --name backend -p 8000:8000 --link mysql:mysql backend-image"

//                     // Run frontend container
//                     sh "docker run -d --name frontend-container --link mysql:mysql -p 5000:5000 frontend-image"
//                 }
//             }
//         }
//     }
// }
 // stages {
    //     stage('Build MySQL Image') {
    //         steps {
    //             script {
    //                 // Build Docker image for MySQL
    //                 docker.build('mysql-image', '-f mysql/Dockerfile ./mysql')
    //             }
    //         }
    //     }
    //     stage('Build Backend Image') {
    //         steps {
    //             script {
    //                 // Build Docker image for the backend service
    //                 docker.build('backend-image', '-f backend/Dockerfile ./backend')
    //             }
    //         }
    //     }
    //     stage('Build Frontend Image') {
    //         steps {
    //             script {
    //                 // Build Docker image for the frontend service
    //                 docker.build('frontend-image', '-f frontend/Dockerfile ./frontend')
    //             }
    //         }
    //     }
      //     }
        // }
//         stage('Run MySQL Container') {
//             steps {
//                 script {
//                     // Run MySQL container
//                     docker.image('mysql-image').withRun('-e MYSQL_ROOT_PASSWORD=jagriti@123 -e MYSQL_DATABASE=employees_db', 'mysql')
//                 }
//             }
//         }
//         stage('Run Backend Container') {
//             steps {
//                 script {
//                     // Run backend container
//                     docker.image('backend-image').withRun('-p 8000:8000 --link mysql:mysql', 'backend-container')
//                 }
//             }
//         }
//         stage('Run Frontend Container') {
//             steps {
//                 script {
//                     // Run frontend container
//                     docker.image('frontend-image').withRun('-p 5000:5000 --link mysql:mysql', 'frontend-container')
//                 }
//             }
//         }
//     }
// }
