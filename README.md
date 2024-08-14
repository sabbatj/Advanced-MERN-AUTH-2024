<h1 align="center">Advanced Auth 🔒 </h1>

![Demo App](/frontend/public/screenshot-for-readme.png)

About This Project:

- 🔐 Signup
- 🔑 Sign In
- 🔄 Forgot Password
- 🔁 Reset Password
- 📧 Email Verification
- 🚪 Logout
- ✔️ JWT Authentication
- 🔒 Route Protection
- 📋 Signup Page UI
- 🔓 Login Page UI
- ✅ Email Verification Page UI
- 🚀 Deployed on Render
- Email handling with Mailtrap.io.
### Setup .env file

```bash
MONGO_URI=your_mongo_uri
PORT=5000
JWT_SECRET=your_secret_key
NODE_ENV=development

MAILTRAP_TOKEN=your_mailtrap_token
MAILTRAP_ENDPOINT=https://send.api.mailtrap.io/

CLIENT_URL= http://localhost:5173
```

### Run this app locally

```shell
npm run build
```

### Start the app

```shell
npm run start
```

### 
How the Auth Flow
##
1. Signup Process
##
🔲 **Signup Page (📋)**
      |
      ▼
🔄 **User enters:**
      🧑‍💻 fullname
      📧 email
      🔒 password
      |
      ▼
🔺 **Clicks "Sign Up" button**
      |
      ▼
🔵 **Email Sent (📧)** 
      - Backend generates a verification code.
      - Saves it in the database along with user data.
      - Sends a verification email using Mailtrap.
      |
      ▼
🔲 **Verification Page (✅)**
      |
      ▼
🔄 **User enters:**
      📋 Verification Code
      |
      ▼
✔️ **Account Verified (✅)** 
      - Backend checks the verification code.
      - If valid, marks user as verified in the database.
      - Redirects user to the login page.
##
2. Login Process
##
🔲 **Login Page (🔓)**
      |
      ▼
🔄 **User enters:**
      📧 email
      🔒 password
      |
      ▼
🔺 **Clicks "Login" button**
      |
      ▼
🔵 **Auth Check (✔️)**
      - Backend validates user credentials.
      - Checks if the account is verified.
      - If valid, generates a JWT token.
      - Sends the token to the frontend.
      |
      ▼
🏠 **Dashboard**
      - User is redirected to the dashboard.
      - The dashboard is protected and only accessible with a valid JWT token.
##
3. Logout Process
##
🔲 **Dashboard**
      |
      ▼
🔺 **Clicks "Logout" button (🚪)**
      |
      ▼
✔️ **Logged Out (✅)**
      - Backend invalidates the JWT token.
      - User is redirected to the login page.
##
4. Forgot Password Process
##
🔲 **Forgot Password Page (🔄)**
      |
      ▼
🔄 **User enters:**
      📧 email
      |
      ▼
🔵 **Email Sent (📧)**
      - Backend generates a reset token.
      - Saves it in the database with an expiry time.
      - Sends a reset password email using Mailtrap.
      |
      ▼
🔲 **Reset Password Page (🔁)**
      - User clicks the reset link in the email.
      - Navigates to the reset password page.
      |
      ▼
🔄 **User enters:**
      🔒 New password
      |
      ▼
✔️ **Password Reset (✅)**
      - Backend validates the reset token.
      - Updates the password in the database.
      - Redirects user to the login page.
##
Backend Setup
🔧 1. Backend Setup
Setup Express.js Server:

Initialize an Express.js server.
Configure middleware for JSON parsing, CORS, and security.
Setup MongoDB Connection:

Connect to a MongoDB database using Mongoose.
Define the user schema with fields for fullname, email, password, isVerified, verificationCode, resetToken, and resetTokenExpiry.
##
🗄️ 2. Database Setup
MongoDB Collections:
Users:
🧑‍💻 fullname: The full name of the user.
📧 email: The email address of the user.
🔒 password: The hashed password.
✅ isVerified: Boolean flag indicating if the user has verified their email.
📋 verificationCode: A unique code sent to the user's email for verification.
🔄 resetToken: A token sent to the user's email for password reset.
⏲️ resetTokenExpiry: The expiry time for the reset token.
