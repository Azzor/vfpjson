- **Now the properties can be any case, not just lowercase.**

- **Now empty arrays are shown like**

"otherServices": []

- **When the arrays were empty they were shown like**
"array": {[false]}

- **Sometimes native VFP properties are unhidden from the JSON object and were shown in the JSON string**

*Many thanks* to Ignacio Gutierrez Torrero!

Awesome program that you did!

Hi from Hermosillo, Mexico!

-
-
-
-
-

#VFPJSON
JSON library for VFP.
**WARNING** Too slow to used with large data


**json_encode(xExpr)**

Returns a string, that is the json of any expression passed.

**json_decode(cJson)**

Returns an object, from the string passed.

**json_getErrorMsg()**

Returns empty if no error found in last decode.

**recordToJson()**

Returns the json representation for current record.

**tableToJson()**

Returns the json representation for current table
Warning need to be changed for large table, because use dimension aInfo[reccount()]
For large table should change to create the string record by record.


###Examples
```
set procedure json additive

oPerson = json_decode(' { "name":"Ignacio" , "lastname":"Gutierrez", "age":33 } ')
if not empty(json_getErrorMsg())
	? 'Error in decode:'+json_getErrorMsg())
	return
endif
? oPerson.get('name') , oPerson.get('lastname')

obj = oJson.decode('{"jsonrpc":"1.0", "id":1, "method":"sumArray", "params":[3.1415,2.14,10],"version":1.0}')
? obj.get('jsonrpc'), obj._jsonrpc
? obj.get('id'), obj._id
? obj.get('method'), obj._method
? obj._Params.array[1], obj._Params.get(1)


cJson = ' {"server":"imap.gmail.com", "user":"billgates", "password":"melinda" , "port":895, "auth":false, "ssl":false, "timeout":20, "error":404}' 
? cJson
oSmtp = json_decode(cJson)
cJson =  json_encode(oSmtp)


? json_encode(_screen)

```
