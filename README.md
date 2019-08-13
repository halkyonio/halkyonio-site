## Halkyon.io web site

This web site is for the moment used to redirect incoming HTTP requests to reply with a `<meta content` tag

Information is available here:
- https://golang.org/cmd/go/#hdr-Remote_import_paths
- https://stackoverflow.com/questions/26347516/using-go-get-on-a-personal-git-repo

Command to be used to deploy and configure the nginx server is 

```
oc project halkyonio-site
oc apply -f configmap.yml
oc apply -f service.yml
oc apply -f deployment.yml
```

Check if we get a meta tag
```bash
curl -svL halkyon.io | grep -i go-import

curl -kL https://halkyon.io/group/project?go-get=1   
<html>
<head><title>404 Not Found</title></head>
<body>
<center><h1>404 Not Found</h1></center>
<hr><center>nginx/1.16.0</center>
</body>
</html>
```
