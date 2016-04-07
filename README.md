JBoss BRMS Suite Cool Store Demo with AngularJS & Patternfly
================================
This is a retail web store demo where you will find rules, decision tables, events, and a ruleflow 
that is leveraged by a single page Angular-based application and protected by [KeyCloak](http://keycloak.jboss.org).

The web application is a WAR built using the JBoss BRMS
generated project as a dependency, providing an example project showing how developers can focus on the 
application code while the business analysts can focus on rules, events, and ruleflows in the 
JBoss BRMS product web based dashboard.

The single page app is housed within the WAR and is built with [AngularJS](https://angularjs.org) and [PatternFly](https://patternfly.org).

This demo is built with, contained by and executed using [Docker](https://docker.com).


Building the Demo with Docker
-----------------------------------------
The following steps can be used to configure and run the demo in a container

1. [Download and unzip.](https://github.com/jbossdemocentral/brms-coolstore-demo/archive/master.zip)

2. Add products [installs directory](installs/).

3. Copy contents of [support/docker](support/docker) directory to the project root.

4. Build demo image

	```
	$ docker-compose build
	```
5. Start demo containers

	```
	$ docker-compose up
	```
		
6. Login to JBoss Business Central at `http://<DOCKER_HOST>:8080/business-central`

    - login for admin and analyst roles (u:`erics` / p:`jbossbrms1!`)
    - Navigate to `Authoring -> Project Authoring -> Open Project Editor -> Build -> Build & Deploy` to deploy the project in BRMS.

7. Login to Keycloak admin console at `http://<DOCKER_HOST>:8181/auth`

   - login for keycloak admin (u:jfalkner / p:keycloak1!)
	- Observe keycloak config (but don't change anything)

8. Open shopping cart and demo away (`http://<DOCKER_HOST>:8080/brms-coolstore-demo`)

	- login for the cool store is (u:`jfalkner` / p:`keycloak1!`)
	
Note that if you are using Docker through VM (e.g. when using Docker on Mac OS X), you will need [forward your localhost ports to the Docker VM](https://github.com/boot2docker/boot2docker/blob/master/doc/WORKAROUNDS.md#port-forwarding).
  
Additional information can be found in the jbossdemocentral container [developer repository](https://github.com/jbossdemocentral/docker-developer)


Notes
-----
The server application (shopping cart) is built during demo installation with a provided coolstore project jar version 2.0.0. When you 
open the project you will find the version is also set to 2.0.0. You can run the web application as is, but if you build and deploy
a new version of 2.0.0 to your maven repository it will find duplicate rules. To demo you deploy a new version of the coolstore
project by bumping the version number on each build and deploy, noting the KieScanner picking up the new version within 10 seconds 
of a new deployment. For example, initially start project, bump the version to 3.0.0, build and deploy, open web application and
watch KieScanner in server logs pick up the 3.0.0 version. Now change a shipping rule value in decision table, save, bump project
version to 4.0.0, build and deploy, watch for KieScanner picking up new 4.0.0 version, now web application on next run will use new
shipping values.


Supporting Articles
-------------------
- [JBoss BRMS Cool Store UI gets Vaadin facelift](http://www.schabell.org/2016/01/jboss-brms-coolstore-ui-vaadin-facelift.html)

- [7 Steps to Your First Rules with JBoss BRMS Starter Kit](http://www.schabell.org/2015/08/7-steps-first-rules-jboss-brms-starter-kit.html)

- [3 shockingly easy ways into JBoss rules, events, planning & BPM](http://www.schabell.org/2015/01/3-shockingly-easy-ways-into-jboss-brms-bpmsuite.html)

- [Jump Start Your Rules, Events, Planning and BPM Today](http://www.schabell.org/2014/12/jump-start-rules-events-planning-bpm-today.html)

- [4 Foolproof Tips Get You Started With JBoss BRMS 6.0.3](http://www.schabell.org/2014/10/4-foolproof-tips-get-started-jboss-brms-603.html)

- [How to Use Rules and Events to Drive JBoss BRMS Cool Store for xPaaS](http://www.schabell.org/2014/08/how-to-use-rules-events-drive-jboss-brms-coolstore-xpaas.html)

- [Red Hat JBoss BRMS - all product demos updated for version 6.0.2.GA release](http://www.schabell.org/2014/07/redhat-jboss-brms-product-demos-6.0.2-updated.html)

- [Red Hat JBoss BRMS 6 - Demo Cool Store Dynamic Rule Updates (video)] (http://www.schabell.org/2014/05/redhat-jboss-brms6-demo-coolstore-dynamic-rule-updates.html)

- [Red Hat JBoss BRMS 6 - The New Cool Store Demo] (http://www.schabell.org/2014/03/redhat-jboss-brms-v6-coolstore-demo.html)
 
- [JBoss BRMS Cool Store Demo updated with EAP 6.1.1] (http://www.schabell.org/2013/09/jboss-brms-coolstore-demo-updated-eap-611.html)

- [A shopping cart example in the Cool Store Demo] (http://www.schabell.org/2013/04/jboss-brms-coolstore-demo.html)

- [Cool Store installation video part I] (http://www.schabell.org/2013/05/jboss-brms-coolstore-demo-video-partI.html)

- [Cool Store CEP and Rules video part II] (http://www.schabell.org/2013/05/jboss-brms-coolstore-demo-video-partII.html)

- [Cool Store BPM and Decision Tables video part III] (http://www.schabell.org/2013/05/jboss-brms-coolstore-demo-video-partIII.html)


Released versions
-----------------
See the tagged releases for the following versions of the product:

- v1.0 Initial version based on the awesome [JBoss Developer Cool Store Vaadin Demo](https://github.com/jbossdemocentral/brms-coolstore-demo)

![Announcement Sign](https://github.com/jbossdemocentral/brms-coolstore-demo/blob/master/docs/demo-images/announce-sign.jpg?raw=true)

[![Video bpmPaaS CoolStore](https://github.com/jbossdemocentral/brms-coolstore-demo/blob/master/docs/demo-images/video-brms-coolstore-demo.png?raw=true)](https://vimeo.com/ericschabell/brms-coolstore-demo)

[![Video bpmPaaS CoolStore](https://github.com/jbossdemocentral/brms-coolstore-demo/blob/master/docs/demo-images/video-bpmpaas-coolstore.png?raw=true)](http://vimeo.com/ericschabell/bpmpaas-brms-coolstore-demo)

![Decision Table](https://github.com/jbossdemocentral/brms-coolstore-demo/blob/master/docs/demo-images/coolstore-decision-table.png?raw=true)

![Domain Model](https://github.com/jbossdemocentral/brms-coolstore-demo/blob/master/docs/demo-images/coolstore-model.png?raw=true)

