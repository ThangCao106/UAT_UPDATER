pipeline {  
    agent any
    stages {
		stage('Confirm') {
		    steps {
			    script {
			    timeout(time: 5, unit: 'MINUTES') {
				def result = input(id: "MoPhien Gate", message: "MoPhien ?", parameters: [[$class: 'BooleanParameterDefinition', defaultValue: true, description: '', ok: 'MoPhien']])
			    echo 'result: ' + result
                 
                if(!userInput) {
                error "Cancel MoPhien PS"
                 }
			      }
		         }
		    }
        }
		stage('Mo phien PS UAT1') {
		    steps {
			    sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2303\", \"ExchangeStatus\": \"O\"}"'
		   
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2304\", \"ExchangeStatus\": \"O\"}"'
            
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2306\", \"ExchangeStatus\": \"O\"}"'
            
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"VN30F2309\", \"ExchangeStatus\": \"O\"}"'
                 }
            }
        }
    }

