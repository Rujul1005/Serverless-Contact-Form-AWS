# 🌐 AWS Serverless Contact Form

## 🚀 Project Overview
This project demonstrates a fully serverless contact form application using AWS cloud services.

The frontend is a static HTML website hosted on Amazon S3. When a user submits the form, data is sent through API Gateway, processed by AWS Lambda, and stored in DynamoDB.

---

## 🧰 Tech Stack
- Amazon S3  
- Amazon API Gateway  
- AWS Lambda  
- Amazon DynamoDB  
- HTML, CSS, JavaScript 
---

## 🏗️ Architecture
User → S3 (HTML Form) → API Gateway → Lambda → DynamoDB  

S3 hosts the static website, API Gateway handles HTTP requests, Lambda processes the data, and DynamoDB stores the form submissions.

---

## ✨ Features
- Serverless backend architecture  
- Static website hosting on AWS S3  
- Real-time form submission handling  
- Data storage in DynamoDB  
- Scalable and cost-efficient design  
---

## 📸 Screenshots
<img width="1403" height="795" alt="Bucket" src="https://github.com/user-attachments/assets/f4322045-1c82-4470-b731-c5a1be34d0f3" />
<img width="1920" height="1080" alt="DynamoDB" src="https://github.com/user-attachments/assets/896cfd58-652f-4735-a443-42fe27a9d1be" />
<img width="1920" height="1080" alt="Lambda Function" src="https://github.com/user-attachments/assets/7b10a554-c574-4683-b062-2957c93895d3" />
<img width="1920" height="1080" alt="Contact Form" src="https://github.com/user-attachments/assets/8948b669-3144-4306-ab4f-3e272eefdfd0" />

---


## 🧠 What I Learned
- Hosting static websites using S3  
- Building serverless APIs using API Gateway  
- Writing AWS Lambda functions for backend logic  
- Working with DynamoDB NoSQL database  
- Integrating frontend with cloud backend services  

---

## ⚙️ Deployment Steps
- Create a DynamoDB table for storing form data  
- Create AWS Lambda function to process requests  
- Configure API Gateway and connect it to Lambda  
- Enable CORS for frontend integration  
- Host frontend HTML file on Amazon S3  
- Test form submission and verify data in DynamoDB 
---

## 🌐 API Endpoint Example
Base URL: https://5t0wyd87ch.execute-api.us-east-1.amazonaws.com
Route: /contact
---

## 📌 Lambda Function Code
    const AWS = require("aws-sdk");  
    const db = new AWS.DynamoDB.DocumentClient();  
    
    exports.handler = async (event) => {  
        const body = JSON.parse(event.body);  
    
        const params = {  
            TableName: "ContactForm",  
            Item: {  
                email: body.email,  
                name: body.name,  
                message: body.message,  
                timestamp: new Date().toISOString()  
            }  
        };  
    
        await db.put(params).promise();  
    
        return {  
            statusCode: 200,  
            body: JSON.stringify({ message: "Data saved successfully!" })  
        };  
    };  

## ⚠️ Note
AWS resources should be monitored to avoid unnecessary billing.  
Ensure proper IAM permissions are configured for Lambda access to DynamoDB.

---

## 💼 Resume Highlight
Built a fully serverless contact form using AWS S3, API Gateway, Lambda, and DynamoDB, enabling scalable form submission processing without managing any backend server.
