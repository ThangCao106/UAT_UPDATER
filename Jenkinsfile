pipeline {  
    agent any
     environment {
                    MaPS1 = 'VN30F2303'
                    MaPS2 = 'VN30F2304'
                    MaPS3 = 'VN30F2306'
                    MaPS4 = 'VN30F2309'
                }
    stages {
		 stage('input OTWS') {
                environment {
                    inputSan = ''
                    inputPhien = ''
                }
                steps {
                    script {

                    def userInput = input( id: 'userInput', message: 'Chon san can chuyen phien:?',
                    parameters: [
                        //string(defaultValue: 'None', description: 'Nhanh can restart', name: 'Nhanh'),
                        choice(name: 'San', choices: ['HOSE', 'HNX','UPCOM','VNFE','HSX_ODDLOT','all'], description: 'San can chuyen phien'),
                        choice(name: 'Phien', choices: ['KLLT', 'ATC', 'ATO'], description: 'Phien can chuyen')
                    ])

                    echo ("San can chuyen:" + userInput.San)
                    echo ("Loai phien can chuyen: " + userInput.Phien)
                    inputSan = userInput.San ?: ''
                    inputPhien= userInput.Phien ?: ''
                    echo ("env Nhanh OTWS restart: ${inputSan}" )
                    echo ("env Loai OTWS restart: ${ inputPhien}" )
                    }
                    }
                }
        stage('Chuyển phiên HOSE KLLT') {
            when {
                allOf {
                    expression { inputSan == 'HOSE' }
                    expression { inputPhien == 'KLLT' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"VN\",\"MarketStatus\": \"O\",\"ChangeMS\":true}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên HOSE KLLT thanh cong!\033[0m'
                }
            }
            }
            stage('Chuyển phiên HOSE ATC') {
            when {
                allOf {
                    expression { inputSan == 'HOSE' }
                    expression { inputPhien == 'ATC' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"VN\",\"MarketStatus\": \"A\"}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên HOSE ATC thanh cong!\033[0m'
                }
            }
            }
            stage('Chuyển phiên HOSE ATO') {
            when {
                allOf {
                    expression { inputSan == 'HOSE' }
                    expression { inputPhien == 'ATO' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"VN\",\"MarketStatus\": \"P\"}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên HOSE ATO thanh cong!\033[0m'
                }
            }
            }
            stage('Chuyển phiên HNX KLLT') {
            when {
                allOf {
                    expression { inputSan == 'HNX' }
                    expression { inputPhien == 'KLLT' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"HNXIndex\",\"MarketStatus\": \"O\"}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên HOSE KLLT thanh cong!\033[0m'
                }
            }
            }
             stage('Chuyển phiên HNX KLLT') {
            when {
                allOf {
                    expression { inputSan == 'HNX' }
                    expression { inputPhien == 'KLLT' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"HNXIndex\",\"MarketStatus\": \"O\"}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên HNX KLLT thanh cong!\033[0m'
                }
            }
            }
            stage('Chuyển phiên HNX ATC') {
            when {
                allOf {
                    expression { inputSan == 'HNX' }
                    expression { inputPhien == 'ATC' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"HNXIndex\",\"MarketStatus\": \"L\"}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên HNX ATC thanh cong!\033[0m'
                }
            }
            }
            //stage UPCOM
             stage('Chuyển phiên UPCOM KLLT') {
            when {
                allOf {
                    expression { inputSan == 'UPCOM' }
                    expression { inputPhien == 'KLLT' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"HNXUpcomIndex\",\"MarketStatus\": \"O\"}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên UPCOM KLLT thanh cong!\033[0m'
                }
            }
            }
            //stage VNFE
            stage('Chuyển phiên VNFE ATC') {
            when {
                allOf {
                    expression { inputSan == 'VNFE' }
                    expression { inputPhien == 'ATC' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\":\"${MaPS1}\", \"ExchangeStatus\": \"Q\"}" && echo "Success" || echo "Failure"' 
		   
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"${MaPS2}\", \"ExchangeStatus\": \"Q\"}" && echo "Success" || echo "Failure"'
            
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"${MaPS3}\", \"ExchangeStatus\": \"Q\"}"&& echo "Success" || echo "Failure"'
            
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"${MaPS4}\", \"ExchangeStatus\": \"Q\"}" && echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên VNFE ATC thanh cong!\033[0m'
                }
            }
            }
            stage('Chuyển phiên VNFE ATC') {
            when {
                allOf {
                    expression { inputSan == 'VNFE' }
                    expression { inputPhien == 'KLLT' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\":\"${MaPS1}\", \"ExchangeStatus\": \"O\"}" && echo "Success" || echo "Failure"' 
		   
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"${MaPS2}\", \"ExchangeStatus\": \"O\"}" && echo "Success" || echo "Failure"'
            
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"${MaPS3}\", \"ExchangeStatus\": \"O\"}"&& echo "Success" || echo "Failure"'
            
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{ \"RType\":\"UpdateStock\", \"StockSymbol\": \"${MaPS4}\", \"ExchangeStatus\": \"O\"}" && echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên VNFE KLLT thanh cong!\033[0m'
                }
            }
            }
            //stage HSX_ODDLOT
            stage('Chuyển phiên HSX_ODDLOT KLLT') {
            when {
                allOf {
                    expression { inputSan == 'HSX_ODDLOT' }
                    expression { inputPhien == 'KLLT' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"HSX_ODDLOT\",\"MarketStatus\": \"O\",\"ChangeMS\":true}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên HSX_ODDLOT KLLT thanh cong!\033[0m'
                }
            }
            }
            stage('Chuyển phiên HSX_ODDLOT ATC') {
            when {
                allOf {
                    expression { inputSan == 'HSX_ODDLOT' }
                    expression { inputPhien == 'ATC' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"HSX_ODDLOT\",\"MarketStatus\": \"A\"}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên HSX_ODDLOT ATC thanh cong!\033[0m'
                }
            }
            }
            stage('Chuyển phiên HSX_ODDLOT ATO') {
            when {
                allOf {
                    expression { inputSan == 'HSX_ODDLOT' }
                    expression { inputPhien == 'ATO' }
                }
            }
            steps {
                sh 'curl "http://192.168.54.7:8880/admin"  -X POST   -d "{\"RType\":\"UpdateIndex\",\"IndexCode\":\"HSX_ODDLOT\",\"MarketStatus\": \"P\"}"&& echo "Success" || echo "Failure"'
            }
            post {
                success {
                    echo -e '\033[32mChuyển phiên HSX_ODDLOT ATO thanh cong!\033[0m'
                }
            }
            }

        }
    }

