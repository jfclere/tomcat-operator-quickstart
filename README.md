# tomcat-operator-quickstart
Quickstart for Tomcat Operator

The repository just demos the use of https://github.com/web-servers/tomcat-s2i it assumes you have built a docker image there and tag it like IMAGE_BUILDER_TAG

Usage

To build a docker image using the tomcat-s2i do the following. Don't forget to start docker before.
```bash
$ git clone https://github.com/jfclere/tomcat-operator-quickstart.git
$ cd tomcat-operator-quickstart
$ export IMAGE_BUILDER_TAG=${USER}/tomcat-s2i
$ export IMAGE_TAG=docker.io/${USER}/tomcat-app
$ s2i build . ${IMAGE_BUILDER_TAG} ${IMAGE_TAG}
```
To test:
```bash
$ docker run -p 8080:8080 ${IMAGE_TAG}
```
To curl the curl
```bash
$ curl http://localhost:8080/
```
To use it with the tomcat operator push it to docker hub and configure the quickstart-cr.yaml accordingly.
```bash
$ docker login docker.io -u ${USER}
$ docker push ${IMAGE_TAG}
```
Edit ./quickstart-cr.yaml ajust the line:
applicationImage: ${IMAGE_TAG}

Install the operator look to https://github.com/web-servers/tomcat-operator for instructions.

On Openshift do:

$ oc create -f quickstart-cr.yaml

On kubernetes do:

$ kubectl create -f quickstart-cr.yaml
