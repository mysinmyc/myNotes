GOLANG MONGO
============


## Connection

````go
package main;

import (
        "gopkg.in/mgo.v2"
)

func main() {
        vSession,vErr:=mgo.Dial("localhost");
        if vErr!=nil {
                panic(vErr);
        }
        defer vSession.Close();

        vCollection:=vSession.DB("myDb").C("myCollection");
}
````


## Atomic Insert

````go
package main;

import (
        "log"
        "gopkg.in/mgo.v2"
)


type MioTipo struct {
        ID int
        Nome string
}

func main() {

        vSession,vErr:=mgo.Dial("localhost");
        if vErr!=nil {
                panic(vErr);
        }
        defer vSession.Close();

        vCollection:= vSession.DB("myDb").C("myCollection");

        vErr=vCollection.Insert(MioTipo{ ID: 1, Nome: "CIAO"});

        if (vErr != nil) {
                log.Fatal(vErr)
        }
}
````
