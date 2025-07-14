# 🔐 Serverless Authentication System

A serverless authentication and authorization system built using AWS Lambda, Amazon Cognito, and API Gateway. This project was developed as part of a college assignment for Distributed Systems, and demonstrates secure user management using JWTs, stateless sessions via cookies, and custom Lambda authorizers

## 📚 Overview
This project enables secure user authentication with the following features:

- 🔑 User Sign Up & Email Confirmation
- 🔐 Secure Sign In with JWT Cookie Handling
- 🚪 User Sign Out with Cookie Expiry
- 🧪 Token Validation via Cognito’s Public Keys
- ✅ API Gateway Lambda Authorizer for Protected Routes
- 🚫 Public Route Access (Unauthenticated)

## 🔄 How It Works
### 🔁 Auth Flow
User → Sign Up → Confirm Email → Sign In → Get JWT → Access Secured APIs

- SignUp: Registers a user and stores in AWS Cognito.
- ConfirmSignUp: Confirms the user's email via a verification code.
- SignIn: Authenticates user and returns a JWT in a secure cookie.
- SignOut: Invalidates the session by expiring the cookie.
- Authorizer: Verifies JWT and applies access policies.
- Secure Lambda: Returns protected content for valid users only.
- Public Lambda: Accessible to anyone.

## 🛠️ Project Structure
```
├── handlers/
│   ├── signup.ts           # User registration with Cognito
│   ├── signin.ts           # User authentication and JWT token issue
│   ├── signout.ts          # Clears token cookie
│   ├── confirmSignUp.ts    # Email confirmation handler
│   ├── authorizer.ts       # API Gateway Lambda authorizer
│   ├── protected.ts        # JWT-secured Lambda function
│   ├── public.ts           # Open-access endpoint
│
├── utils/
│   ├── utils.ts            # Cookie parsing, token verification, policy generation
│
├── shared/
│   ├── types.ts            # Type definitions for API payloads
│   ├── types.schema.json   # JSON schema for validation (used with Ajv)
```

## ⚙️ Installation & Setup
1. Clone the repository

- ```git clone https://github.com/your-username/distributed-auth-system.git```
- ```cd distributed-auth-system```

2. Install dependencies
- ```npm install```

3. Configure environment variables
Set these in your deployment config (e.g., .env, Lambda environment, or SAM config):
- REGION
- USER_POOL_ID
- CLIENT_ID

4. Deploy using your preferred serverless framework
- AWS SAM, Serverless Framework, or manual Lambda configuration

## ✅ Features & Status

| Feature                         | Status         |
| ------------------------------- | -------------- |
| User Registration (Sign Up)     | ✔️ Implemented |
| Email Confirmation              | ✔️ Implemented |
| JWT Token Handling (Sign In)    | ✔️ Implemented |
| Secure Cookie Management        | ✔️ Implemented |
| API Gateway Custom Authorizer   | ✔️ Implemented |
| Protected Lambda Endpoint       | ✔️ Implemented |
| Public (Open) Lambda Endpoint   | ✔️ Implemented |
| Sign Out Handler                | ✔️ Implemented |
| Schema-based Payload Validation | ✔️ Implemented |

## 📦 Dependencies
- aws-sdk & @aws-sdk/client-cognito-identity-provider
- jsonwebtoken
- jwk-to-pem
- axios
- ajv (for schema validation)

## 💡 Useful commands

* `npm run build`   compile typescript to js
* `npm run watch`   watch for changes and compile
* `npm run test`    perform the jest unit tests
* `cdk deploy`      deploy this stack to your default AWS account/region
* `cdk diff`        compare deployed stack with current state
* `cdk synth`       emits the synthesized CloudFormation template
