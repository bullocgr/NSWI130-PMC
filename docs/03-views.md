## Views

### How are the views documented?

The software architecture of PMC is further documented according to the [C4 model](https://c4model.com/) using its 2 levels - [container](https://c4model.com/#ContainerDiagram) level and [component](https://c4model.com/#ComponentDiagram) level.
The documentation also uses supplementary diagrams - [deployment diagrams](https://c4model.com/#DeploymentDiagram) and [dynamic diagrams](https://c4model.com/#DynamicDiagram).

### PMC Decomposition View
#### PMC Decomposition View - Container Level

PMC business functionality is implemented by the PMC Server container.
Doctors interact with a web application provided by MPC Web Front-end container.
The server container uses the Patients Real Time Data System to read and write prescriptions into the database. The corrects prescriptions are directly provided to the PMC Server by the Barcode Scanner. 


![](embed:PMC_Container_View)

#### PMC Decomposition View - Component Level

PMC Server implements the business functionality of PMC.
Its internal architecture comprises 3 layers:
* Domain Model represents the business domain of PMC which is data sets and their distributions. Its components represent the domain as a basic object model with simple get/set operations.
* Business Logic implements all the business logic on top of the domain model.
* Infrastructure implements the interaction with the other containers through APIs and gateways.

![](embed:PMC_Server_Component_View)

### PMC Dynamic View
#### Hospitalization System Dynamic View

The patients register to get in the hospital, consequently the list of patients is updated. Then doctors can write a new prescription using the barcode scanner. Finally, the PMC treats the request to write it in the database.

![](embed:Hospitalization_System_Dynamic_View)

#### Vital Signs Component Dynamic View
In a more detail, the Vital Signs Monitering Component informs the Data reader to fetch lastest data, so it sends the request to the Data system which returns the latest data to the Data Reader which will transmit it to the Vital Signs Monitering Component to analyze. Finally, Vital Signs Monitering Component will inform the Patient API to send an emergency alert to the Web Front-end if necessary.

![](embed:Vitals_Signs_Component_Dynamic_View)

#### #Doctor Check Component Dynamic View
In a more detail, the Patient API informs the Data reader to fetch lastest data, so it sends the request to the Data system which returns the latest data to the Data Reader which will transmit it to the Patient API. Finally, the Patient API will send an emergency alert the Web Front-end if necessary.

![](embed:#Doctor_Check_Component_Dynamic_View)

### PMC Deployment View
![](embed:PatientMonitoringandControlPMC-Live-Deployment)
