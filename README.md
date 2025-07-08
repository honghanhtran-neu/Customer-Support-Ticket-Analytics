# Customer Support Ticket Analytics

## 1. Business Context
The company operates a **multi-channel customer support system** (including chat, phone, social media, email) to handle technical issues and service requests from customers. Each customer request is logged in the system as a support ticket.
However, the current system lacks visibility in several key areas:
- Overall status and volume of incoming tickets
- Response and resolution speed across channels, products, and issue types
- Satisfaction levels of customers by time, channel, or product
This lack of visibility makes it difficult for the company to **measure performance, identify bottlenecks, and make data-driven decisions** to enhance the customer experience.

## 2. Key Business Questions
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

## 3. Data Understanding
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

*These missing values are mostly found in open or pending tickets that haven't been resolved yet.*

🧾 **Column Summary**
Below is a brief overview of the main columns:
- Ticket ID: Unique identifier for each support request
- Customer Name / Email / Age / Gender: Customer demographics
- Product Purchased: Name of the purchased item
- Date of Purchase: Date of transaction (currently in string format)
- Ticket Type / Subject / Description: Nature of the issue
- Ticket Status: Current status (Closed, Open, Pending)
- Resolution: Final resolution (often missing)
- Ticket Priority: Level of urgency (Low → Critical)
- Ticket Channel: Contact method (Email, Chat, Phone, Social Media)
- First Response Time: When support responded (string format)
- Time to Resolution: When issue was resolved (string format)
- Customer Satisfaction Rating: Feedback score (1–5)

🧠 **Key Insights**
- No structural issues like corrupted records or duplicate rows were found.
- Missing values are informative and expected for unresolved tickets.
- Date/time fields are inconsistently formatted and must be standardized.
- Ticket priority and channel could be key drivers in predicting response/resolution time.

## 4. Data Cleaning & Preprocessing

✅ Data Type Handling
- Converted date-related fields to proper datetime format, enabling accurate time-based analysis such as resolution time calculations.

🧹 Text Cleaning
- Cleaned and lemmatized the Ticket Description and Resolution columns to standardize text and prepare for further NLP analysis or clustering.
- This allows for improved understanding of common customer issues and support responses.

❓ Missing Values
- Missing values in key fields like Resolution, First Response Time, and Customer Satisfaction Rating were labeled (instead of filled) to retain the context (e.g., unresolved tickets or ongoing cases).
- This tagging supports more accurate filtering and modeling later on.

🕒 Time-Based Features
- Created a new feature to measure the handling time between first response and final resolution.
- Identified unexpected patterns where some tickets were resolved before any recorded response, suggesting differences in workflow or urgency depending on ticket type or channel.
- These patterns may indicate:
  - Automated backend resolutions,
  - Customer support prioritization behavior,
  - Or delayed communication to customers.

## 5. Exploratory Data Analysis (EDA)
### 5.1. Univariate Analysis

**Customer Age Distribution**
- The distribution is relatively uniform across age groups from 18 to 70.
- Slight dips in some age bins may be due to sampling or market penetration gaps.

**Customer Gender Distribution**
- The gender distribution is balanced across all three categories: Female, Male, and Other.
- Indicates inclusivity or neutrality in customer engagement.

**Ticket Type Frequency**
- Most common issues include Refund Requests and Technical Issues.
- Billing Inquiries and Product Inquiries are slightly less frequent, suggesting relatively fewer product-related complaints or confusion.

**Ticket Channel Distribution**
- All support channels are used relatively equally: Email, Phone, Social Media, and Chat.
- This implies customers have diverse preferences when reaching out to support.

**Customer Satisfaction Ratings**
- The ratings are nearly uniformly distributed from 1 to 5.
- Suggests inconsistency in service quality or high variation across different ticket types and agents.

**Handling Time (First Response → Resolution)**
- The distribution of handling time is approximately normal but slightly skewed to the right.
- A significant number of tickets show negative handling time, meaning resolutions occurred before the first customer response.
