GOLANG HTTP
===========


## HTTP server



````go
package main

import (
        "log"
        "io"
        "net/http"
)

func myHandler (pResponseWriter http.ResponseWriter, pRequest *http.Request) {
        io.WriteString(pResponseWriter,"OK baby");
}

func main() {
        http.HandleFunc("/",myHandler);
        log.Fatal(http.ListenAndServe(":8080",nil));
}
````

### TLS

In case of TLS use `http.ListenAndServeTLS(":8080", "/tmp/cert.pem", "/tmp/key.pem", nil)`

Key pair can be generated by using `cd /tmp; go run $GOROOT/src/crypto/tls/generate_cert.go --host localhost`
