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
6. Create Fiori Elements App:
   - Template: List Report Object Page
   - Data Source: OData V2
   - Service URL: [/V2/Northwind/Northwind.svc/](https://services.odata.org/v2/northwind/northwind.svc/) 
7. Run the app:
   ```bash
   npm start

-------------------------------------

4- OData Entity Used

Entity: Products

Reason:The Products entity provides meaningful business data such as product name, price, and stock levels, making it suitable for demonstrating Fiori List Report capabilities.

-------------------------------------

5- Challenges Faced:

1. Object Page Not Displaying Data
  Issue: Object Page opened but showed empty content
  Solution: Attempted multiple annotation configurations; issue likely due to missing backend annotations in the public OData service
2. Deployment URL Not Accessible
 Issue: Application deployed but not accessible publicly
 Solution: Identified that SAP Build Work Zone subscription is required, which is not available in trial
3. Git Authentication Issues
  Issue: BAS failed to authenticate with GitHub
  Solution: Used Personal Access Token with remote URL configuration.

-------------------------------------

6- Bonus Tasks Completed

-B1 
   




