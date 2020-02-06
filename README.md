# Build Pageflow inside a Docker Container #

This Repo is based on the great Open Source Framework Pageflow, which you can find here: [https://github.com/codevise/pageflow](https://github.com/codevise/pageflow)

## 1. Get Pageflow running in 4 Steps ##

```bash
$ git clone https://github.com/ElasticBrains/docker-pageflow.git
$ cd docker-pageflow/pageflow
$ docker build -t pf:1.0 .
$ docker run --rm -it -p 3000:3000 pf:1.0
```

In the `docker run` command pageflow will be installed, this could take a while. Wait until you see the RubyOnRails output in your terminal. Which should look something like this:

```
=> Booting WEBrick
=> Rails 4.2.8 application starting in development on http://0.0.0.0:3000
=> Run `rails server -h` for more startup options
=> Ctrl-C to shutdown server
[2017-06-14 14:15:42] INFO  WEBrick 1.3.1
[2017-06-14 14:15:42] INFO  ruby 2.3.4 (2017-03-30) [x86_64-linux]
[2017-06-14 14:15:42] INFO  WEBrick::HTTPServer#start: pid=24 port=3000
```

Then you should be able to call http://localhost:3000 in your web browser. Please note that the first Request you make to Pageflow by Browser will take around 10 seconds until you see the Web View.

The default User from pageflows `rake db:seed` is

```
     email:     admin@example.com
     password:  !Pass123
```

## 2. But Wait!! ##

Pageflow isn't running properly! This is becuase of several things we still need to do:


1. Set up external Services, and find a Solution to combine this smart with Dockerfile. Following this instructions: [https://github.com/codevise/pageflow/wiki/Setting-up-External-Services](https://github.com/codevise/pageflow/wiki/Setting-up-External-Services)
2. Maybe it would be a good idea to outsource the database and redis with a docker-compose.yaml

Only then we can use the full power of Pageflow

## 3. Running Pageflow ##

1. Insert your AWS and Zencoder Credentials in the credentials file before you run the docker run command
2. You still need to set up the AWS S3-Buckets and Zencoder in order to get everything to work!

## 4. Customizing Pageflow ##

Customize your Pageflow and add new plugins and page-types according to:
[https://github.com/codevise/pageflow/wiki](https://github.com/codevise/pageflow/wiki#extending-pageflow)

