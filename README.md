# django-minikube
Set up a Django application and deploy on Kubernetes environment using Minikube.

# Requirements
+ [Install Docker](https://docs.docker.com/engine/installation/)
+ Minikube
+ Django 1.9.7

# Run command

## Build Django Image
#### Build Base Image: Django and Python3.6
	```
	$ cd django-minikube/devops
	$ docker build -t nhatthai/python3.6_django  .
	```

#### Build App:
	```
	$ cd backend
	$ docker build -t nhatthai/mysite_django .
	```

#### Push to Docker Hub
	```
	docker push nhatthai/mysite_django:latest
	```

### Start Minikube
	```
	$ minikube start
	```

### Create Deployment
	```
	$ cd devops/manifest
	$ kubectl create -f deployment.yml
	```

### Create Service
	```
	$ cd devops/manifest
	$ kubectl create -f service.yml
	```

### Ingress
#### Create Ingress
```
$ cd devops/manifest
$ kubectl create -f ingress.yml
```

#### Check Ingress status
```
kubectl describe ing
```

#### Start Ingress on Minkube
```
$ minikube addons enable ingress
```

#### Get IP
```
$ minikube ip
192.168.99.100
```

#### Add mysite.com into /etc/hosts
```
192.168.99.100 mysite.com
```

#### Check Django App
```
http://mysite.com/admin/
```

# Reference
[Writing your first Django App](https://docs.djangoproject.com/en/2.1/intro/tutorial01/)
