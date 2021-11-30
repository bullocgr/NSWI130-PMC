## Views

### How are the views documented?

The software architecture of PMC is further documented according to the [C4 model](https://c4model.com/) using its 2 levels - [container](https://c4model.com/#ContainerDiagram) level and [component](https://c4model.com/#ComponentDiagram) level.
The documentation also uses supplementary diagrams - [deployment diagrams](https://c4model.com/#DeploymentDiagram) and [dynamic diagrams](https://c4model.com/#DynamicDiagram).

### PMC Decomposition View

PMC business functionality is implemented by the PMC Server container.
Doctors interact with a web application provided by MPC Web Front-end container.
The server container uses the Patients Real Time Data System to read and write prescriptions into the database. The corrects prescriptions are directly provided to the PMC Server by the Barcode Scanner. 


![](embed:PMC_Container_View)

### PMC Server Decomposition View

PMC Server implements the business functionality of PMC.
Its internal architecture comprises 3 layers:
* Domain Model represents the business domain of PMC which is data sets and their distributions. Its components represent the domain as a basic object model with simple get/set operations.
* Business Logic implements all the business logic on top of the domain model.
* Infrastructure implements the interaction with the other containers through APIs and gateways.

![](embed:PMC_Server_Component_View)

### Hospitalization System Dynamic Views

The patients register to get in the hospital, consequently the list of patients is updated. Then the Data System informs the PMC of a new patient, so that doctors can write a new prescription using the barcode scanner. Finally, the PMC treats the request and give the prescription to the Data system to write it in the database.

![](embed:Hospitalization_System_Dynamic_View)

#### MPC Containers Dynamic Views
In a more detail, the Patient API informs the Data reader to fetch lastest data, so it sends the request to the Data system which returns the latest data to the Data Reader which will transmit it to the Patient API. Finally, the Patient API will send an emergency alert the Web Front-end if necessary.


![](embed:Vitals_Signs_Component_Dynamic_View)

### MPC Deployments

There exist various MPC deployment environments. (which we don't have yet :)

#### MPC Server Development Deployment

(This deployment is mandatory for all NODC Server developers and their unit tests.)

![](embed:Server_Development_Deployment)

#### MPC Live Deployment

(This deployment is the current production environment of NODC.)

![](embed:Live_Deployment)
