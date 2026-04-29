# 🚀 Serverless Contact Form using AWS

A fully serverless contact form web application built using AWS. Users submit data from a static website hosted on S3, and the data is processed and stored in the cloud without any backend server.

## ⚙️ Tech Stack
AWS S3 (Static Website Hosting), AWS API Gateway (REST API), AWS Lambda (Serverless Backend), AWS DynamoDB (NoSQL Database)

## 🧠 Architecture
Frontend → API Gateway → Lambda → DynamoDB

## 🚀 Features
- Fully serverless architecture  
- Static website hosted on AWS S3  
- Stores form submissions in DynamoDB  
- Scalable and cost-efficient backend  
- Simple HTML/CSS/JS frontend

## 📸 Screenshots
<img width="1403" height="795" alt="Bucket" src="https://github.com/user-attachments/assets/f4322045-1c82-4470-b731-c5a1be34d0f3" />
<img width="1920" height="1080" alt="DynamoDB" src="https://github.com/user-attachments/assets/896cfd58-652f-4735-a443-42fe27a9d1be" />
<img width="1920" height="1080" alt="Lambda Function" src="https://github.com/user-attachments/assets/7b10a554-c574-4683-b062-2957c93895d3" />
<img width="1920" height="1080" alt="Contact Form" src="https://github.com/user-attachments/assets/8948b669-3144-4306-ab4f-3e272eefdfd0" />

---

## 🔧 How It Works
1. User submits form on website  
2. Request is sent to API Gateway  
3. API Gateway triggers AWS Lambda function  
4. Lambda processes data and stores it in DynamoDB  
5. Data is saved and visible in AWS console  

## 🌐 API Endpoint Example
POST https://your-api-id.execute-api.region.amazonaws.com/contact  

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

## 🧪 AWS Services Used
- Amazon S3 → Hosting static website  
- Amazon API Gateway → API layer  
- AWS Lambda → Backend logic  
- Amazon DynamoDB → Database  

## 💡 What I Learned
- Serverless architecture using AWS  
- API Gateway + Lambda integration  
- Working with DynamoDB NoSQL database  
- Hosting static websites using S3  

## ⚠️ Note
AWS resources were removed to avoid billing charges.  
Screenshots are provided as proof of deployment.

---


## 💼 Resume Highlight
Built a serverless contact form using AWS S3, API Gateway, Lambda, and DynamoDB to process and store user data without a backend server.
