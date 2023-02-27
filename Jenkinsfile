pipeline {  
    agent any
     def runComment = true;
    try {
        // In the console logs
        // Will ask you to Proceed a release (60 sconds temporisation)
        // after 60s runRelease is evaluated to false in exception block
        timeout(time: 60, unit: 'SECONDS') {
            input 'Ban co muon mo phien (Yes/No)?'
        }
    } catch (err) {
        runComment = false;
        def user = err.getCauses()[0].getUser()
        if('SYSTEM' == user.toString()) { // SYSTEM means timeout.
            echo "Bỏ qua bởi System (timeout)"
        } else {
            echo "Bỏ qua bởi: [${user}]"
        }
    }

    if(runRelease) {
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
}
