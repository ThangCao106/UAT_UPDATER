pipeline {  
    agent any
    stages {
		stage('Mo phien PS UAT ') {
		    steps {
			sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2303\", \"ExchangeStatus\": \"O\"}"'
		    }
		}
		stage('Mo phien PS UAT ') {
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2304\", \"ExchangeStatus\": \"O\"}"'
            }
        }
		stage('Mo phien PS UAT ') {
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2306\", \"ExchangeStatus\": \"O\"}"'
            }
        }
		stage('Mo phien PS UAT ') {
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2309\", \"ExchangeStatus\": \"O\"}"'
            }
        }
    }
}
