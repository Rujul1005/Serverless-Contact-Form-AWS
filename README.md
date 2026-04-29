# 🚀 Serverless Contact Form using AWS

A fully serverless contact form web application built using AWS. Users submit data from a static website hosted on S3, and the data is processed and stored in the cloud without any backend server.

## ⚙️ Tech Stack
AWS S3 (Static Website Hosting), AWS API Gateway (REST API), AWS Lambda (Serverless Backend), AWS DynamoDB (NoSQL Database)

## 🧠 Architecture
Frontend → API Gateway → Lambda → DynamoDB

## 📁 Project Structure
frontend/ (index.html, style.css, script.js)  
lambda/ (index.js)

## 🚀 Features
- Fully serverless architecture  
- Static website hosted on AWS S3  
- Stores form submissions in DynamoDB  
- Scalable and cost-efficient backend  
- Simple HTML/CSS/JS frontend  

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

## 🔥 Future Improvements
- Add email notifications using AWS SNS  
- Improve UI with frameworks like React  
- Add authentication system  
- Add form validation and security layers  

## 👨‍💻 Author
Built as part of Cloud Computing learning journey 🚀
