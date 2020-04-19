# tomcat-operator-quickstart
Quickstart for Tomcat Operator

The repository just demos the use of https://github.com/web-servers/tomcat-s2i it assumes you have built a docker image there and tag it like IMAGE_BUILDER_TAG

Usage

To build a docker image using the tomcat-s2i do the following.

$ s2i build . [IMAGE_BUILDER_TAG] [IMAGE_TAG]

To test:

$ docker run -p 8080:8080 [IMAGE_TAG]

To curl the curl

$ curl http://localhost:8080/

To use it with the tomcat operator push it to docker hub and configure the quickstart-cr.yaml accordingly.

applicationImage: "[IMAGE_TAG]

Install the operator look to https://github.com/web-servers/tomcat-operator for instructions.

On Openshift do:

$ oc create -f quickstart-cr.yaml

On kubernetes do:

$ kubectl create -f quickstart-cr.yaml
