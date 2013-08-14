# Simple Hello World app ready for Cloud Foundry

To deploy:

```
$ cf push
Using manifest file manifest.yml

Custom startup command> none

Creating hello... OK

1: hello
2: none
Subdomain> hello

1: mypaas.com
2: none
Domain> mypaas.com

Binding hello.mypaas.com to hello... OK
Uploading hello... OK
Starting hello... OK
-----> Downloaded app package (4.0K)
Installing ruby.
-----> Using Ruby version: ruby-1.9.2
-----> Installing dependencies using Bundler version 1.3.2
       Running: bundle install --without development:test --path vendor/bundle --binstubs vendor/bundle/bin --deployment
       Fetching gem metadata from https://rubygems.org/..........
       Installing rack (1.5.2)
       Using bundler (1.3.2)
       Your bundle is complete! It was installed into ./vendor/bundle
       Cleaning up the bundler cache.
-----> Uploading staged droplet (24M)
-----> Uploaded droplet
Checking hello...
Staging in progress...
  0/1 instances: 1 starting
  0/1 instances: 1 starting
  1/1 instances: 1 running
OK

$ curl hello.mypaas.com
Hello World!
```



Note about proxy configuration :

 you could adapt the push :
```
  cf --http-proxy http://myproxy.myproxydomain:8080 --https-proxy http://myproxy.myproxydomain:8080 push
```
 and change the manifest.yml by appending this lines :
```
   env:
    HTTP_PROXY: myproxy.myproxydomain:8080
    HTTPS_PROXY: myproxy.myproxydomain:8080
```
