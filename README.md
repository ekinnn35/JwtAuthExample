
# 🔐 JwtAuthExample

## 📌 Overview

This is a simple ASP.NET Core Web API project demonstrating how to implement JWT (JSON Web Token) based authentication. The project includes user login functionality and protects API endpoints using `[Authorize]` attributes.

---

## 🚀 Features

- ✅ Register and Login with Email & Password
- ✅ JWT Token Generation on Login
- ✅ JWT Token Validation
- ✅ Secure API Endpoints
- ✅ Entity Framework Core for user persistence
- ✅ Model Validation with `[Required]`, `[EmailAddress]`

---

## 📂 Project Structure

```
JwtAuthExample/
│
├── Controllers/
│   └── AuthController.cs
│
├── Models/
│   └── User.cs
│
├── Data/
│   └── ApplicationDbContext.cs
│
├── Services/
│   └── TokenService.cs
│
├── Program.cs
├── appsettings.json
└── README.md
```

---

## 📦 Technologies Used

- ASP.NET Core 8.0
- Entity Framework Core (Code First)
- JWT Bearer Authentication
- Fluent Validation
- Swagger UI for testing

---

## 🔄 API Endpoints

### 👤 Register
**POST** `/api/auth/register`  
**Body:**
```json
{
  "email": "user@example.com",
  "password": "MySecurePassword123"
}
```

---

### 🔐 Login
**POST** `/api/auth/login`  
**Body:**
```json
{
  "email": "user@example.com",
  "password": "MySecurePassword123"
}
```

**Returns:**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
}
```

---

### 🔒 Protected Endpoint (Example)
**GET** `/api/secure/data`  
**Header:**
```
Authorization: Bearer {your_token_here}
```

---

## 🧠 JWT Token Setup

- Token generation is handled in `TokenService.cs`
- Configuration in `Program.cs`:
```csharp
builder.Services.AddAuthentication(JwtBearerDefaults.AuthenticationScheme)
    .AddJwtBearer(options => {
        options.TokenValidationParameters = new TokenValidationParameters {
            ValidateIssuer = true,
            ValidateAudience = true,
            ValidateLifetime = true,
            ValidateIssuerSigningKey = true,
            ValidIssuer = "JwtAuthExampleAPI",
            ValidAudience = "JwtAuthExampleUser",
            IssuerSigningKey = new SymmetricSecurityKey(Encoding.UTF8.GetBytes("your_super_secret_key"))
        };
    });
```

---

## ▶️ Getting Started

### 1. Clone the repository
```bash
git clone https://github.com/your-username/JwtAuthExample.git
cd JwtAuthExample
```

### 2. Run with Visual Studio
- Open `JwtAuthExample.sln`
- Press **F5** to run
- Swagger UI will open at `https://localhost:xxxx/swagger`

---

## 📝 Notes

- Make sure to update `appsettings.json` with your own secret key for production use.
- This project uses an In-Memory database for demonstration. Switch to SQL Server or SQLite for real use cases.

---
