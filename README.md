# win10pro-rhel8-minikube-dev

## Configure minikube
> Default 2Gb sometimes not enough, so set 4Gb for memory

```
minikube config set memory 4096
```

> We want minikube to have registry and metric server. First we start minikube with minimum option

```
minikube start
```

```
minikube addons enable registry
```

```
minikube addons enable metrics-server
```

> Stop and start with additional options

```
minikube stop
```

```
minikube start --insecure-registry localhost:5000 --vm-driver=kvm2 --apiserver-ips=<host-ip-address> --extra-config=kubelet.housekeeping-interval=10s
```

## Configure Haproxy

> Sometimes we want to access the minikube resources from another machine, in this case we setup ha proxy

For simple setup, allow haproxy to listen to any port

```
sudo setsebool -P haproxy_connect_any on
```

## TODO

> At some point maybe automate this instruction
