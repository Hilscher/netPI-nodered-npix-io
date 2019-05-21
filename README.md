## Node-RED + DIO nodes

Made for [netPI](https://www.netiot.com/netpi/), the Raspberry Pi 3B Architecture based industrial suited Open Edge Connectivity Ecosystem

### Debian with Node-RED and DIO nodes for NIOT-E-NPIX-4DI4DO expansion module

The image provided hereunder deploys a container with installed Debian, Node-RED and dio nodes to communicate with expansion modules NIOT-E-NPIX-4DI4DO.

Base of this image builds [debian](https://www.balena.io/docs/reference/base-images/base-images/) with installed Internet of Things flow-based programming web-tool [Node-RED](https://nodered.org/) and two extra nodes *dio in/out* providing access to the 4 digital input and 4 digital output signals of the module NIOT-E-NPIX-4DI4DO over the GPIOs 22,23,25,26, 4, 14, 15, 17 and 27.

ATTENTION! Never plug or unplug any extension module if netPI is powered. Make sure a module is already inserted before applying 24VDC to netPI. 

#### Container prerequisites

##### Port mapping

To allow the access to the Node-RED programming tool over a web browser the container TCP port `1880` needs to be exposed to the host.

##### Privileged mode

Only the privileged mode option lifts the enforced container limitations to allow usage of GPIOs in a container needed for the nodes *dio in/out*.

#### Getting started

STEP 1. Open netPI's landing page under `https://<netpi's ip address>`.

STEP 2. Click the Docker tile to open the [Portainer.io](http://portainer.io/) Docker management user interface.

STEP 3. Enter the following parameters under **Containers > Add Container**

* **Image**: `hilschernetpi/netpi-nodered-npix-io`

* **Port mapping**: `Host "1880" (any unused one) -> Container "1880"` 

* **Restart policy"** : `always`

* **Runtime > Privileged mode** : `On`

STEP 4. Press the button **Actions > Start/Deploy container**

Pulling the image may take a while (5-10mins). Sometimes it takes so long that a time out is indicated. In this case repeat the **Actions > Start/Deploy container** action.

#### Accessing

After starting the container open Node-RED in your browser with `http://<netpi's ip address>:<mapped host port>` e.g. `http://192.168.0.1:1880`. Two extra nodes *dio in/out* in the nodes *npix* library provides you access to the 4 digital input and 4 digital output of the NPIX module. The nodes' info tab in Node-RED explains how to use them.

#### Automated build

The project complies with the scripting based [Dockerfile](https://docs.docker.com/engine/reference/builder/) method to build the image output file. Using this method is a precondition for an [automated](https://docs.docker.com/docker-hub/builds/) web based build process on DockerHub platform.

DockerHub web platform is x86 CPU based, but an ARM CPU coded output file is needed for Raspberry systems. This is why the Dockerfile includes the [balena](https://balena.io/blog/building-arm-containers-on-any-x86-machine-even-dockerhub/) steps.

#### License

View the license information for the software in the project. As with all Docker images, these likely also contain other software which may be under other licenses (such as Bash, etc from the base distribution, along with any direct or indirect dependencies of the primary software being contained).
As for any pre-built image usage, it is the image user's responsibility to ensure that any use of this image complies with any relevant licenses for all software contained within.

[![N|Solid](http://www.hilscher.com/fileadmin/templates/doctima_2013/resources/Images/logo_hilscher.png)](http://www.hilscher.com)  Hilscher Gesellschaft fuer Systemautomation mbH  www.hilscher.com
