1. 
```
docker build -t jervis/nginx .
```

2. 
```
docker run -d -p 8080 --name website -v $PWD/website:/var/www/html/website:ro jervis/nginx
```

3. 
```
docker ps -a
```

4. 
```
curl localhost:32772
```