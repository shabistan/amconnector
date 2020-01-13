# ESTABLISHING A CONNECTION WITHIN ACUMATICA
After the package has been published, the connector must be established within Acumatica
## CONFIGURING THE CONNECTOR IN ACUMATICA
The first step in configuring the Magento Connector is to setup the parameters of the connector. Navigate to the Magento Connector workspace and click Setup Parameters. Navigate to the Connection Settings section.

1.Enter the Magento URL.

    a.This is the store URL for the Magento eCommerce website.
 
2.Enter the **Bearer Token**.

    a.The Bearer Token can be found on the Magento site.
 
     i.Navigate to the System workspace on the Magento Site.
  
     ii.Click Integrations under the Extensions workspace.
  
     iii.Click the Pencil Icon next to the ACE integration.
  
      iv.The Bearer Token will be listed under the Access Token field.
  
    b.Enter the Bearer Token again to Confirm Bearer Token.
 
3.Click **Test Connection**.

    a.A success message will render if the connection is successful.
    
 ![](C:\Users\shabistanf\Desktop\Images\image.png)
 
 Next, navigate to the **Queue Processing Settings** section.
 
 1.Enter a **Threshold Count**.
 
    a.The Threshold Count value indicates the number of records that will be sent individually from Acumatica to Magento prior to the records being batched. (e.g. if there are 50 records being sent, and the threshold count is 25, then the records are batched by using the count defined in the Batch count value and sent to Magento. If the batch count defined is for 25, then Acumatica batches 25 messages in one request and makes only 2 requests to Magento.) This setting is applicable only for the Pricing and Inventory sync.
    
2.Enter a **Batch Count**.

    a.	The batch count value indicates how many records will be added to an FTP call for bulk record sync. This reduces sync time by making multiple, smaller FTP calls. (e.g. if syncing 50 records, the threshold count is set to 25, and the batch count is set to 5, the 50 records will be sent in 10 API calls, each containing 5 records to be synced.). This setting is applicable only for the Pricing and Inventory sync.
    
3.Enter a **Retry Count**.
   
    a. This value is the number of times Acumatica attempts to send across a message to Magento before rendering them as a Failed message. All failed messages are not attempted automatically by the application. To process any Failed messages, you can use the Reprocess Failed Messages screen in the Magento Connector workplace.
 
4.Enter a **Check Process Time**.

    a. The accepted value for this option is between 1 and 59. This value defines the frequency in number of seconds for which a schedule once initiated by the framework continues to execute. All schedulers defined by the Magento Connector are scheduled to run every 1 minute. This setting is an extension of the default scheduling to define if the process should be slowed down and controlled. When the framework initiates a scheduler as per the defined schedules, the scheduler first completes the designated task. It then checks for the time for which the process should continue to run based on the already elapsed time versus the defined check process time. If the already elapsed time is less than the Check process time, then the scheduler thread continues to run until the time it has elapsed the time defined in the Check Process time. 
  
5.Enter a **Process Sleep Time**.

    a.	This value is the time between check processes in seconds. (e.g. if the check process time is set to 50 seconds, and the process sleep time is set to 5 seconds, the connector will first finish the expected tasks when it launches. Once the task is completed, it sleeps for the defined amount of time and then checks for any new records to be processed. This setting is controlled by the Check Process Time setting above.

 ![](C:\Users\shabistanf\Desktop\Images\image 2.png)
 
 If utilizing the Commerce Pro package, a section will appear in the Setup Parameters screen that will be unique to this package: Price Sync Preferences.
 
 1.Toggle the selection of price to sync with the connector
 
    a.	Default Price
    b.	Sales Price

     i.	The Sales Price of the item is listed on the stock item screen. This can be configured during the configuration of the CommercePro Package.
     
Next, navigate to the **Inventory Sync Preferences**. 

1.	If using the CommercePro Package, toggle the selection of the Inventory sync preference that you’d wish to use.

       a.Execute Sync based on Branch-wise inventory sync definition in CommercePro.
       
        i.Branch-wise inventory allows for the maintaining and tracking of inventory on a branch by branch basis. This option will allow a user to allocate inventories by branch.
        
       b.Execute sync based on following configuration.
       
        i.Select the monitor and Publish settings for Quantity. This is the value that gets published to Magento as the default available quantity for a product
        
1.	Quantity Available

2.	Quantity Available for Shipping

3.	Quantity Available on Hand

       ii.Select the warehouse(s) to be monitored by the connector.
       
       iii.Select the Magento Sync quantity value. If the CommercePro package is not published, the only fields available in this section are listed in steps 1bi-1biii.

Navigate to the **Vendor Inventory Preferences** section. This section is available only when the CommercePro package is published.

1.Select a vendor inventory sync preference.

    a.This section offers options on how to show available vendor inventories from Acumatica to Magento. Vendor inventory quantities can be included as a separate value in Magento or as a part of the overall inventory quantity in Magento.
    
Navigate to the **Shipment Sync Trigger** section.

1.Select a shipment sync trigger.

       a.Shipments will sync between Acumatica and Magento based on the selection of the setting on this screen. Shipment syncs will occur on the shipment confirmation or on the invoice release.
       
Navigate to the **A to M Customer Sync Preferences** section.

1.	Select the Customer Class(es) that will be synced with Magento.

Navigate to the **A to M Order Sync Preferences** section.

1.	Select the Order Type(s) that will be synced with Magento.

Navigate to the **A to M Dropship ShipVia Sync Preferences** section.

1.	Select a ShipVia method for Dropship orders.

       a.A ShipVia method must be selected for Dropship orders to ensure proper syncs from Acumatica to Magento. By default, Magento does not have a shipping method to represent Dropship shipments. This allows a user to define a customer shipping method in Magento and then map it with the defined incoming value from Acumatica.
       
Navigate to the **Additional Settings** section.

1.Toggle the Enable Customer Attribute Sync to Magento box.

       a.This feature will allow for customer attributes to sync to Magento from Acumatica.

**Note**:  Customer Attributes are available and supported only with Magento Enterprise Edition.	
Navigate to the Individual Sync Status section. This section allows a user to toggle on the type of sync that will occur based on the business need.

1.Toggle on the Active box next to the entity that needs to be enabled for sync.

When all preferences have been configured, click **Save**.
