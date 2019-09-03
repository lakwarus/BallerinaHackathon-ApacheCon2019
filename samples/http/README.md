#### HTTP client sample
```
$> ballerina run http_client.bal 
GET request:
{"args":{"test":"123"}, "headers":{"x-forwarded-proto":"https", "host":"postman-echo.com", "user-agent":"ballerina/1.0.0-alpha3", "x-forwarded-port":"443"}, "url":"https://postman-echo.com/get?test=123"}


POST request:
{"args":{}, "data":"POST: Hello World", "files":{}, "form":{}, "headers":{"x-forwarded-proto":"https", "host":"postman-echo.com", "content-length":"17", "content-type":"text/plain", "user-agent":"ballerina/1.0.0-alpha3", "x-forwarded-port":"443"}, "json":null, "url":"https://postman-echo.com/post"}


DELETE request:
{"args":{}, "data":"DELETE: Hello World", "files":{}, "form":{}, "headers":{"x-forwarded-proto":"https", "host":"postman-echo.com", "content-length":"19", "content-type":"text/plain", "user-agent":"ballerina/1.0.0-alpha3", "x-forwarded-port":"443"}, "json":null, "url":"https://postman-echo.com/delete"}


Content-Type: application/json; charset=utf-8
Status code: 20
```

#### Access the service (basic_01)
```
$ curl -v localhost:9090/hello/sayHello

Hello, World!
```

#### Access the service (basic_02)
```
$ curl -v http://localhost:9090/foo/bar -d "{\"hello\": \"world\"}" -H "Content-Type: application/json"

{"hello": "world"}
```

#### Access the service (data_binding)
```
$ curl -v http://localhost:9090/hello/bindJson -d '{ "Details": { "ID": "77999", "Name": "XYZ"} , "Location": { "No": "01", "City": "Colombo"}}' -H "Content-Type:application/json"

{"ID":"77999","Name":"XYZ"}

$ curl -v http://localhost:9090/hello/bindStruct -d '{ "Name": "John", "Grade": 12, "Marks": {"English" : "85", "IT" : "100"}}' -H "Content-Type:application/json"

{"Name":"John","Grade":12}
```

#### Access the service (passthrough)
```
$ curl http://localhost:9090/passthrough -X POST
Hello World!
$ curl http://localhost:9090/passthrough -X GET
Hello World!
$ curl http://localhost:9090/passthrough -X PUT
Hello World!
```
