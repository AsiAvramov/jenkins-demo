pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                echo 'שלב 1: שיבוט קוד מגיטהאב'
                checkout scm
            }
        }

        stage('Install') {
            steps {
                echo 'שלב 2: התקנת תלויות'
                sh 'npm install'
            }
        }

        stage('Test') {
            steps {
                echo 'שלב 3: הרצת טסטים'
                sh 'npm test'
            }
        }

        stage('Deploy') {
            when {
                branch 'main'
            }
            steps {
                echo 'שלב 4: פריסה (רק ב-main)'
                // כאן אפשר לשים פקודות SSH / SCP / Docker
            }
        }
    }

    post {
        success {
            echo 'הפייפליין הסתיים בהצלחה 🎉'
        }
        failure {
            echo 'הפייפליין נכשל ❌'
        }
    }
}
