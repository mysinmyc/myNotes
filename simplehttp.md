Simple HTTP servers and clients
===============================


# Test

## CURL TO POST A JSON

````
curl -d @-  -H "Content-Type: application/json" -X POST  http://127.0.0.1:5000/paperino <<EOF
{
"scrivo":"CIAO"
}
EOF
````



## HTTPIE TO POST A JSON

`http --json post  http://127.0.0.1:5000/paperino scrivo=ciao`


# Python

## Base HTTPServer

it's embedded in python distributions

````python

from BaseHTTPServer import HTTPServer,BaseHTTPRequestHandler

class MyHandler(BaseHTTPRequestHandler):
        def do_GET(self):
                self.wfile.write("<html><body>hello</body></html>")

if __name__ == "__main__":
	vServer = HTTPServer(('0.0.0.0', 5555),MyHandler)
	vServer.serve_forever()


````




## Flask http server 

very simple to make rest api!!! it's BSD lincensed

[Flask Website) (http://flask.pocoo.org/)

it's optional (in ubuntu `apt-get install python-flask`)

handlers are simple methods with a decorator


````python

from flask import Flask,jsonify

app = Flask(__name__)



@app.route("/greetings/<vUser>")
def users(vUser):
	return jsonify({"hello" :  vUser, 'stuff':[ 'bla','bla','bla']})

if __name__ == "__main__":
    app.run('0.0.0.0',5555)


````


## request http client

It's optional (in ubuntu `apt-get install python-requests`)

