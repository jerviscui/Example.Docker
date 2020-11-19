1. 
```
docker build -t jervis/consul .
```

2. 
```
docker run -p 8500:8500 -p 53:53/udp -h node1 jervis/consul -server -bootstrap
```
