# Vehicle_Status_Workflow_Requirements

## 1.  Customer Intake 
- **Rule:** Every workflow starts with a client profile.  
- **Constraints:** Requires `tenantId`, `fullName`, and `mobileNumber`.  
  Optional: `email`, `address`, `companyName`, `taxNumber`.  
- **Safeguard:** Duplicate `mobileNumber` or `email` under the same tenant blocks creation.  
- **Retention:** Deletion triggers soft delete (`isArchived: true`), keeping history intact.  



## 2.  Vehicle Assignment 
- **Rule:** A vehicle must always link to a customer.  
- **Constraints:** Requires `customerId`, `registrationNumber`, `make`, `model`.  
  Optional: `vin`, `engineType`, `fuelType`, `transmission`, `odometer`.  
- **Safeguard:** Duplicate check runs on both `registrationNumber` and `vin`.  



## 3. Job Card Activation 
- **Rule:** Job Card connects Customer and Vehicle, serving as the garage entry point.  
- **Constraints:** Requires `customerId`, `vehicleId`, and `customerComplaint`.  
  Optional: `assignedMechanicId`, `diagnosisSummary`.  
- **Safeguard:** All new job cards default to `status = 'DRAFT'`.  



## 4. Quotation Track 
- **Rule:** Quotes provide itemized estimates before work begins.  
- **Constraints:** Linked via `jobId`. Line items (`QuoteLineDto`) must be `'PART'` or `'LABOR'`.  
  Auto‑adds 15% tax.  
- **Safeguard:** Generates a secure `publicToken` for mobile approval via  
  `/api/public/quotes/:token/approve`.  



## 5. Status Workflow 
- **Rule:** Status mirrors the car’s progress in the shop.  
- **Constraints:** Updates only via `PATCH /api/jobs/:id/status`.  
  Flow: `DRAFT ➔ IN_PROGRESS ➔ WAITING_FOR_PARTS ➔ COMPLETED`.  
- **Safeguard:** Every change logs to `JobStatusHistory` with  
  `fromStatus`, `toStatus`, `changedByUserId`, and `createdAt`.  

