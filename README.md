# Customer Support Ticket Analytics

## 1. Business Context 🧠
The company operates a **multi-channel customer support system** (including chat, phone, social media, email) to handle technical issues and service requests from customers. Each customer request is logged in the system as a support ticket.
However, the current system lacks visibility in several key areas:
- Overall status and volume of incoming tickets
- Response and resolution speed across channels, products, and issue types
- Satisfaction levels of customers by time, channel, or product
This lack of visibility makes it difficult for the company to **measure performance, identify bottlenecks, and make data-driven decisions** to enhance the customer experience.

## 2. Key Business Questions 🎯
To support relevant departments such as the **Head of Customer Support, Product Managers**, and the **CRM/Marketing Team** in enhancing their performance and uncovering actionable trends, this project aims to address the following key business questions:

📌 **Operational Performance**
- What is the average time taken to respond to and resolve a ticket?
- What percentage of tickets are resolved within SLA targets?
- Are high-priority tickets actually being prioritized in practice?

⚠️ **Bottlenecks**
- Which support channels tend to have slower response times?
- Are there recurring issues or frequently reported product-related complaints?

😊 **Customer Experience**
- How does customer satisfaction vary across different products, channels, or time periods?
- Can we predict which tickets are at risk of receiving low satisfaction scores?

📈 **Trends and Seasonality**
- Are there specific months with unusually high ticket volumes?
- How has customer behavior changed between 2020 and 2021?

## 3. Data Understanding 🔍
✅ **Dataset Overview**
- Shape: 8,469 rows × 17 columns
- Duplicate rows: None
- Date fields are in string format and need to be parsed into proper datetime objects for analysis.

🔎 **Missing Data**
Several important columns contain a significant number of missing values:
| Column                        | Null Values | % Missing |
|------------------------------|-------------|-----------|
| Resolution                   | 5,700       | ~67.3%    |
| First Response Time          | 2,819       | ~33.3%    |
| Time to Resolution           | 5,700       | ~67.3%    |
| Customer Satisfaction Rating | 5,700       | ~67.3%    |

These missing values are mostly found in open or pending tickets that haven't been resolved yet.
🧾 **Column Summary**
Below is a brief overview of the main columns:
- Ticket ID: Unique identifier for each support request
- Customer Name / Email / Age / Gender: Customer demographics
- Product Purchased: Name of the purchased item
- Date of Purchase: Date of transaction (currently in string format)
- Ticket Type / Subject / Description: Nature of the issue
- Ticket Status: Current status (e.g., Closed, Open)
- Resolution: Final resolution (often missing)
- Ticket Priority: Level of urgency (Low → Critical)
- Ticket Channel: Contact method (Email, Chat, Phone...)
- First Response Time: When support responded (string format)
- Time to Resolution: When issue was resolved (string format)
- Customer Satisfaction Rating: Feedback score (1–5)

🧠 **Key Insights**
- No structural issues like corrupted records or duplicate rows were found.
- Missing values are informative and expected for unresolved tickets.
- Date/time fields are inconsistently formatted and must be standardized.
- Ticket priority and channel could be key drivers in predicting response/resolution time.
