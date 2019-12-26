[(참고도서)도커/쿠버네티스를 활용한 컨테이너 개발 실전 입문](https://wikibook.co.kr/docker-kubernetes/)

1. sample source file (golang)
```
package main

import (
	"fmt"
	"log"
	"net/http"
)

func main() {
	http.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
		log.Println("received request")
		fmt.Fprintf(w, "Hello Docker!!")
	})

	log.Println("start server")
	server := &http.Server{Addr: ":8080"}
	if err := server.ListenAndServe(); err != nil {
		log.Println(err)
	}
}
```

2. Docker file(filename : Dockerfile-test)
```
FROM golang:1.9

RUN mkdir /echo
COPY main.go /echo

CMD ["go", "run", "/echo/main.go"]
```

3. build docker container
```
$ docker image build -f Dockerfile-test example/echo:latest .
```

4. run docker container(Background, port forwarding)
```
$ docker container run -d -p 9000:8080 example/echo:latest 
```

5. stop docker container
```
docker stop $(docker container ls --filter "ancestor=example/echo" -q)
```
