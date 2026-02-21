# UserPortal — Windows Desktop Application

A professional Windows Forms application built with .NET 8 and SQLite.

## Features
- **Register** — Create a new account with name, email, username & password
- **Login** — Secure sign-in with username or email + password (BCrypt hashed)
- **Dashboard** — Overview of account status, last login, and profile completeness
- **My Profile** — View and update personal details (name, email, phone, address)
- **Security** — Change your password securely
- **Logout** — Session-based authentication

## Tech Stack
| Component | Technology |
|-----------|------------|
| Framework | .NET 8 Windows Forms |
| Database  | SQLite (via Microsoft.Data.Sqlite) |
| Password  | BCrypt.Net-Next (secure hashing) |
| Language  | C# 12 |

## Database
SQLite database is automatically created at:
```
%APPDATA%\UserManagementApp\users.db
```
No setup or installation needed — it's fully self-contained!

---

## How to Build & Run

### Prerequisites
- Windows 10/11
- [.NET 8 SDK](https://dotnet.microsoft.com/en-us/download/dotnet/8.0)

### Steps

1. **Extract** this folder anywhere on your PC.

2. **Open Terminal** (Command Prompt or PowerShell) in the project folder.

3. **Restore packages** and build:
   ```cmd
   dotnet restore
   dotnet build
   ```

4. **Run the app:**
   ```cmd
   dotnet run
   ```

5. **Or publish as a standalone .exe:**
   ```cmd
   dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -o ./publish
   ```
   Your `.exe` will be in the `./publish` folder — share it and run it on any Windows machine!

---

## Project Structure

```
UserManagementApp/
├── Program.cs                    ← Entry point
├── UserManagementApp.csproj      ← Project config + NuGet packages
├── Models/
│   └── User.cs                   ← User data model
├── Data/
│   └── DatabaseHelper.cs         ← All SQLite DB operations
├── Helpers/
│   ├── UIHelper.cs               ← Colors, fonts, shared controls
│   └── SessionManager.cs         ← Login session state
└── Forms/
    ├── LoginForm.cs              ← Sign-in screen
    ├── RegisterForm.cs           ← Create account screen
    ├── DashboardForm.cs          ← Main window with sidebar
    ├── DashboardPage.cs          ← Home/overview panel
    ├── ProfilePage.cs            ← Edit profile panel
    └── SecurityPage.cs           ← Change password panel
```

---

## Screenshots (description)
- **Login screen**: Split-panel with branded left sidebar + clean white login form
- **Register screen**: Same split design with full registration form
- **Dashboard**: Dark sidebar navigation + stats cards + account overview
- **Profile page**: Edit all user fields with live validation
- **Security page**: Change password with strength hints

---

## Build as .exe (Quick Reference)

```powershell
# One-liner for standalone EXE
dotnet publish -c Release -r win-x64 --self-contained true -p:PublishSingleFile=true -o ./publish
```

Run `UserManagementApp.exe` from the `publish` folder. No .NET install needed on the target machine!
