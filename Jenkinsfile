pipeline {
    agent { label 'NODE1_DOTNET6' }
    stages {
        stage ('Clone or Pull') {
            steps {
                git url: 'https://github.com/learndevopsgit/MusicStore.git',
                    branch: 'main'
            }
        }
        stage ('Package') {
            steps {
                sh 'dotnet restore ./MusicStore/MusicStore.csproj && dotnet build ./MusicStore/MusicStore.csproj'
            }
        }
        stage('test') {
            steps {
                sh 'dotnet test --logger "junit;LogFilePath=TEST-musicstoretest.xml" ./MusicStoreTest/MusicStoreTest.csproj'
                junit testResults: '**/TEST-*.xml'
            }
        }
    }
    
}