# Networking 네트워킹

## 네트워킹의 기본 4단계 프로세스
~~~swift
func performRequest(with urlString: String) {
        
        // 1. URL(struct) 인스턴스 생성
        guard let url = URL(string: urlString) else { return }
        
        // 2. URLSession(class) 객체 생성
        let session = URLSession(configuration: .default)
        
        // 3. URLSession에 작업 할당
        let task = session.dataTask(with: url) { data, response, error in
            
            // 3-1. 에러 확인
            if error != nil {
                self.delegate?.didFailWithError(error: error!)
                return
            }
            
            // 3-2. 데이터 확인 및 Parsing
            if let safeData = data {
                if let weather = self.parseJSON(safeData) {
                    delegate?.didUpdateWeather(self, weather: weather)
                }
            }

            // 3-3. response 확인
        }
        
        // 4. 작업 시작
        task.resume()
    }
~~~