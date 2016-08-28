GOLANG SERIALIZATION
======



## Serialization / json

by default public fields of structs are managed

````go
package main

import (
        "log"
        "fmt"
        "encoding/json"
)

type MyType struct {
        Id int `json:"ID"`
        Name string `json:"Name"`
        Value string `json:"-"`
}

func (self MyType) String() string {
        return fmt.Sprintf("id: %d name: %s",self.Id,self.Name);
}

func main() {

        vMyInstance := MyType { Id:1, Name:"ciao", Value:"Miao"};
        vJson,_:=json.Marshal(vMyInstance);
        fmt.Println("MASRHAL OK: ",string(vJson));

        var vUmarshalled MyType;
        vUnMarshalError := json.Unmarshal([]byte("{\"ID\":2,\"NAME\":\"PIPPO\"}"),&vUmarshalled);

        if (vUnMarshalError != nil) {
                log.Fatal("ERROR DURING UNMARSHAL: ",vUnMarshalError);
        }
        fmt.Println("UNMARSHAL OK: ",vUmarshalled);
}

````





## Serialization / XML

````go
package main


import (
        "log"
        "fmt"
        "encoding/xml"
)


type MyType struct {
        XMLName   xml.Name `xml:"myXml"`
        Id int `xml:"id,attr"`
        Name string `xml:"name,attr"`
        Value string `xml:"-"`
}

func (self MyType) String() string {
        return fmt.Sprintf("id: %d name: %s",self.Id,self.Name);
}

func main() {

        vMyInstance := MyType { Id:1, Name:"ciao", Value:"Miao"};
        vJson,_:=xml.Marshal(vMyInstance);
        fmt.Println("MASRHAL OK: ",string(vJson));

        var vUmarshalled MyType;
        vUnMarshalError := xml.Unmarshal([]byte("<myXml id=\"5\" name=\"cinque\"/>"),&vUmarshalled);

        if (vUnMarshalError != nil) {
                log.Fatal("ERROR DURING UNMARSHAL: ",vUnMarshalError);
        }
        fmt.Println("UNMARSHAL OK: ",vUmarshalled);
}
````
