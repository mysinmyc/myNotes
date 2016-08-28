Tips for HTTP
=============


# Test

## CURL TO POST A JSON

````sh
curl -d @-  -H "Content-Type: application/json" -X POST  http://127.0.0.1:5000/paperino <<EOF
{
"scrivo":"CIAO"
}
EOF
````



## HTTPIE TO POST DATA

`http --json post  http://127.0.0.1:5000/paperino scrivo=ciao`



## Apache Benchmark
 - installation `apt-get install apache2-utils`
 - execution `ab -n 0.
  -c {concurrent} {url}`



## Siege benchmark tool


`siege -d 1 -c 2  -t 10s --log=/tmp/siege_$$.log http://localhost:8080`
