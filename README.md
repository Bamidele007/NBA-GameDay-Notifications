# Game Day Notification System

## **Project Overview**
This project is a real-time game day notification system designed to deliver game updates to subscribed users through SMS or email. It leverages **AWS SNS**, **AWS Lambda**, **Amazon EventBridge**, and external sports APIs to ensure users receive timely and accurate notifications. The solution showcases cloud integration, automation, and efficient event-driven processing.

---

## **Features**
- Fetches live sports game data using a reliable API.
- Sends game updates to subscribers via AWS SNS (SMS/Email).
- Automates notification scheduling using Amazon EventBridge.
- Adheres to best practices for security using least privilege IAM roles.

## **Prerequisites**
- API subscription with a valid API key from a sports data provider [sportsdata.io](https://sportsdata.io/)).
- AWS account with a basic understanding of cloud services and Python programming.

---

## **Technical Architecture**
*This section should include a clear description or visual representation of the architecture, focusing on how AWS SNS, Lambda, and EventBridge interact to deliver notifications.*

---

## **Technologies Used**
- **Cloud Provider**: AWS
- **Core Services**: SNS, Lambda, EventBridge
- **Programming Language**: Python 3.x
- **External API**: Sports data API
- **IAM Policies**: Custom least-privilege policies for Lambda and SNS

---

## **Project Structure**
```bash
project-root/
├── src/
│   ├── Lambda_Notifications.py         
├── policies/                        
│   └── SNS_Notification_policy.json    
├── .gitignore
└── README.md                           
```

---

## **Setup Instructions**

### **1. Clone the Repository**
```bash
git clone https://github.com/yourusername/project-repo.git
cd project-repo
```

### **2. Create an SNS Topic**
1. Open AWS Management Console and navigate to SNS.
2. Create a topic (e.g., `game_notifications`) and note the ARN.
3. Add subscriptions for SMS and/or email by providing valid contact details.

### **3. Define IAM Policies and Roles**
1. Create a policy for SNS publishing:
   - Use the JSON from `policies/sns_policy.json`, replacing placeholders with your AWS region and account ID.
2. Create an IAM role for Lambda execution:
   - Attach the SNS policy and AWSLambdaBasicExecutionRole to the role.

### **4. Deploy the Lambda Function**
1. In the AWS Lambda console, create a new function with Python 3.x as the runtime.
2. Assign the IAM role created earlier.
3. Upload or paste the content of `src/notifications_lambda.py` into the code editor.
4. Add required environment variables:
   - `API_KEY`: Your sports data API key
   - `SNS_TOPIC_ARN`: The ARN of the SNS topic created.

### **5. Schedule Notifications with EventBridge**
1. Create a rule in EventBridge with a schedule (e.g., hourly updates).
2. Set the Lambda function as the target.

---

## **Testing**
1. Use the Lambda console to create a test event and invoke the function.
2. Verify notifications via SMS or email.

---

## **Key Takeaways**
1. Implemented a scalable notification system with AWS services.
2. Secured the system using tailored IAM roles.
3. Automated workflows with EventBridge for regular updates.
4. Integrated external APIs for real-time data fetching.

---

