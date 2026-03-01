
## Project: Sales Data Integration & Distribution Pipeline

<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/403abf23-017a-4b9c-8f16-3f1a289757e1" />  


**The Challenge:** A department manager ("Nathan") was manually extracting weekly sales data from a legacy database, sorting orders by status, and manually updating both Airtable and Discord. This process was time-consuming and prone to calculation errors.

**The Solution:**
I built an automated n8n pipeline that synchronizes the legacy system with modern collaboration tools.  


**Key Features & Workflow Logic:**
- **Data Extraction:** Used the HTTP Request Node to interface with a REST API and pull raw JSON sales data.
- **Status Filtering:** Implemented If Nodes to split data into "Booked" vs. "Processing" streams.
- **Data Cleaning:** Used Edit Fields to sanitize "Processing" data, ensuring only orderID and employeeName reach the Airtable destination to maintain data privacy/cleanliness.
- **Custom JavaScript Logic:** Wrote a Code Node to calculate the aggregate sum and count of "Booked" orders using JavaScript.
- **Multi-Channel Output:** Integrated Airtable for record-keeping and Discord for real-time team notifications.
  

  
**Technical Skills Demonstrated:**
- API Authentication & HTTP Methods.
- Data transformation and Schema mapping.
- Writing n8n-compatible JavaScript for custom data processing.
- Third-party credential management (Airtable/Discord).

  
**Code Highlight**  
**Developer Note:** To handle the sum calculation efficiently, I used a custom JS snippet:
```javascript
let items = $input.all(); 
let itemsBooked = items.length;
let bookedSum = 0;
for (let i = 0; i < items.length; i++) {
  bookedSum += items[i].json.orderPrice;
}
return [{json: {itemsBooked, bookedSum} }]
```

  

**Note: This is the project from the n8n Text Courses - Level 1: Beginner course**  
Link Here: https://docs.n8n.io/courses/level-one/
