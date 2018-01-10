pipeline {
    agent { label 'scanner' }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'docker build -t raspberry-sane-git .'
            }
        }
        stage('Test') {
            steps {
                sh 'docker run -v /dev/bus/usb:/dev/bus/usb --privileged raspberry-sane-git scanimage -V'
                sh 'docker run -v /dev/bus/usb:/dev/bus/usb --privileged raspberry-sane-git scanimage -L'
                sh 'docker run -v /dev/bus/usb:/dev/bus/usb --privileged raspberry-sane-git scanimage --mode gray --source TPU8x10 --resolution 600 --format tiff > test.tiff'
                archive 'test.tiff'
            }
        }
        stage('Push') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
