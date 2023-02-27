pipeline {  
    agent any
    stages {
		stage('Confirm') {
		    steps {
			    script {
			      timeout(time: 5, unit: 'MINUTES') {
				input(id: "MoPhien Gate", message: "MoPhien ?", ok: 'MoPhien')
			      }
		         }
		    }
        }
		stage('Mo phien PS UAT1') {
		    steps {
			sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2303\", \"ExchangeStatus\": \"O\"}"'
		    }
		}
		stage('Mo phien PS UAT2 ') {
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2304\", \"ExchangeStatus\": \"O\"}"'
            }
        }
		stage('Mo phien PS UAT3 ') {
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2306\", \"ExchangeStatus\": \"O\"}"'
            }
        }
		stage('Mo phien PS UAT4 ') {
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2309\", \"ExchangeStatus\": \"O\"}"'
                 }
            }
        }
    }

