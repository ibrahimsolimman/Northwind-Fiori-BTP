- SAP BTP Northwind Fiori Application

1- Project Description :
This project is an SAP Fiori Elements application developed on SAP Business Technology Platform (BTP).  
It consumes the Northwind OData V2 service to display product data in a List Report interface with basic navigation to an Object Page.

-------------------------------------

2- Architecture Overview :
The application follows a standard SAP BTP architecture:

- SAP Business Application Studio (BAS) is used for development
- SAP BTP Destination connects the app to the external Northwind OData service
- The Fiori application consumes data through this destination
- Deployment is done using Multi-Target Application (MTA) to Cloud Foundry

-------------------------------------

3- Setup Instructions :

1. Create SAP BTP Trial Account  
2. Enable Cloud Foundry environment  
3. Create a space (dev)  
4. Subscribe to Business Application Studio  
5. Create a Destination:
   - Name: Northwind
   - URL: https://services.odata.org
   - Proxy Type: Internet
   - Authentication: No Authentication
   - Screenshots of [Destination](docs/destination.png)
   
7. Create Fiori Elements App:
   - Template: List Report Object Page
   - Data Source: OData V2
   - Service URL: [/V2/Northwind/Northwind.svc/](https://services.odata.org/v2/northwind/northwind.svc/)
8. Run the app:
   ```bash
   npm start.

- Screenshots of [BAS Preview](docs/bas-preview.png)

-------------------------------------

4- OData Entity Used

Entity: Products

Reason:The Products entity provides meaningful business data such as product name, price, and stock levels, making it suitable for demonstrating Fiori List Report capabilities.

-------------------------------------

5- Challenges Faced:

1. Object Page Not Displaying Data
  -Issue: Object Page opened but showed empty content
  -Solution: Attempted multiple annotation configurations; issue likely due to missing backend annotations in the public OData service
2. Deployment URL Not Accessible
 -Issue: Application deployed but not accessible publicly
 -Solution: Identified that SAP Build Work Zone subscription is required, which is not available in trial
  workzone unsubscription in (docs/workzone-info.png) (docs/subscription-instance.png)
4. Git Authentication Issues
  -Issue: BAS failed to authenticate with GitHub
  -Solution: Used Personal Access Token with remote URL configuration.

-------------------------------------

6- Bonus Tasks Completed

B1 - Deploy to Cloud Foundry
The application was successfully deployed to the Cloud Foundry environment using MTA.
Steps performed:
- Built the MTA archive using `mbt build`
- Deployed using `cf deploy`
- Verified deployment via `cf apps`
Note: The application was deployed successfully, but public access requires SAP Build Work Zone subscription.

- Screenshots of [CF Apps](docs/deployment_finished_cf-apps.png)

---

 B2 - OData Testing via Postman
The Northwind OData service was tested using Postman.
The following query options were successfully demonstrated:
- `$top` → limited number of records
- `$filter` → filtered products by price
- `$select` → retrieved specific fields only
- `$orderby` → sorted products
Screenshots of all queries are included in `/docs`.

*** Postman link : [https://ibrahimsolimman-1800525.postman.co/workspace/e899a941-0a2c-4582-8973-924062b5c8c5/collection/53657876-14a5d90d-2553-4c3e-9f2c-bb22a8dd1887?action=share&source=copy-link&creator=53657876](https://ibrahimsolimman-1800525.postman.co/workspace/e899a941-0a2c-4582-8973-924062b5c8c5/collection/53657876-14a5d90d-2553-4c3e-9f2c-bb22a8dd1887)

---

 B4 - Fiori Object Page
Navigation from List Report to Object Page was successfully implemented.
- Clicking a product opens a detail page of record
- Basic structure is working and object page open showin product details
- Screenshots of [Object Page](docs/object-page.png)

---

 B5 - OData POST Operation
A POST request was successfully executed using a writable OData demo service.
- Created a new product record via Postman
- Verified response returned the created entity
Request and response screenshots are included in `/docs`.

---

* Not Completed

#### B3 - XSUAA Authentication
Not implemented due to lack of a publicly accessible application URL.

#### B6 - SAP Build Work Zone
Not completed because subscription is not available in SAP BTP trial environment. 
   




