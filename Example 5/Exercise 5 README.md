# Exercise 5

We have a mongo-express application and a mongoDB application.  
The mongoDB application is an internal application.  
Tne mongo-express application is an external application.  
The mongoDB credentials are stored in Secrets.  
Tne mongoDB url is stored in ConfigMap.  

## Create the Secret

``type: Opaque`` means the value as to be encoded in base64

```powershell
$Text = ‘This is a secret and should be hidden’
$Bytes = [System.Text.Encoding]::Unicode.GetBytes($Text)
$EncodedText =[Convert]::ToBase64String($Bytes)
$EncodedText
```
