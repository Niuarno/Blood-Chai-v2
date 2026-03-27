# BloodChai - Blood Donation Platform for Bangladesh

A comprehensive blood donation platform connecting donors with those in need across Bangladesh.

## 🚀 Deploy to Vercel via GitHub Desktop

### Step 1: Create GitHub Repository
1. Open GitHub Desktop
2. File → New Repository → Name it `bloodchai`
3. **Don't initialize** with README (we have one)
4. Create the repository

### Step 2: Copy Files
1. Extract this ZIP file
2. Copy ALL files to your new repository folder

### Step 3: Commit and Push
1. Open GitHub Desktop
2. You'll see all files listed
3. Write a commit message like "Initial commit"
4. Click "Commit to main"
5. Click "Publish repository" (make it private or public)

### Step 4: Connect to Vercel
1. Go to [vercel.com](https://vercel.com)
2. Sign in with GitHub
3. Click "New Project"
4. Import your `bloodchai` repository
5. Configure environment variables (see below)
6. Click "Deploy"

---

## ⚙️ Environment Variables for Vercel

Add these in Vercel Dashboard → Settings → Environment Variables:

```
DATABASE_URL=postgresql://postgres:[YOUR-PASSWORD]@db.[YOUR-PROJECT-REF].supabase.co:5432/postgres
NEXTAUTH_SECRET=your-random-32-character-secret-key-here
NEXTAUTH_URL=https://your-app-name.vercel.app
```

**Generate NEXTAUTH_SECRET:**
- Run in terminal: `openssl rand -base64 32`
- Or use: https://generate-secret.vercel.app/32

---

## 🌱 Seed Database from Browser (IMPORTANT!)

After your site is deployed on Vercel, you MUST seed the database to create the admin user.

### Method 1: Visit Seed URL Directly
1. Open your browser
2. Go to: `https://your-app-name.vercel.app/api/seed`
3. You'll see the admin credentials in the response

### Method 2: Use Browser Console
1. Open your deployed site
2. Press F12 (Open Developer Tools)
3. Go to Console tab
4. Paste this code and press Enter:

```javascript
fetch('/api/seed')
  .then(r => r.json())
  .then(data => {
    console.log('═══════════════════════════════════════════');
    console.log('🌱 SEED RESULT:');
    console.log('═══════════════════════════════════════════');
    console.log(JSON.stringify(data, null, 2));
    console.log('═══════════════════════════════════════════');
  })
  .catch(err => console.error('Error:', err));
```

---

## 🔐 Admin Login Credentials

After seeding, use these to login:

| Field | Value |
|-------|-------|
| **Email** | `admin@bloodchai.org` |
| **Password** | `admin123` |

⚠️ **Change the password immediately after first login!**

---

## 📁 Project Structure

```
bloodchai/
├── prisma/           # Database schema & seed
├── public/           # Static files
├── src/
│   ├── app/          # Pages & API routes
│   │   ├── (auth)/   # Login, Register, Become Donor
│   │   ├── admin/    # Admin Dashboard
│   │   ├── donor/    # Donor Dashboard
│   │   ├── recipient/# Recipient Dashboard
│   │   └── api/      # API Endpoints
│   ├── components/   # React Components
│   ├── hooks/        # Custom Hooks
│   └── lib/          # Utilities
├── package.json
└── next.config.ts
```

---

## 🗄️ Database Setup (Supabase)

1. Go to [supabase.com](https://supabase.com)
2. Create a new project
3. Go to Settings → Database
4. Copy the Connection String (URI)
5. Paste as `DATABASE_URL` in Vercel environment variables

**Note:** The database schema will be automatically created when you deploy.

---

## 📱 Features

### For Donors
- Register with blood group and location
- Toggle availability status
- View and respond to blood requests
- Track donation history and reward points

### For Recipients
- Search donors by blood group and location
- Send blood requests to specific donors
- Report problematic donors

### For Admins
- Dashboard with statistics
- Manage users, requests, emergencies
- Create notices
- Configure payment methods (bKash, Nagad, Bank)
- Update site footer information

---

## 🇧🇩 Bangladesh Specific

- **8 Divisions:** Dhaka, Chittagong, Rajshahi, Khulna, Sylhet, Barisal, Rangpur, Mymensingh
- **64 Districts** supported
- **Local Payments:** bKash, Nagad, Bank Transfer

---

## 🔧 Troubleshooting

### "Admin login not working"
1. Make sure you visited `/api/seed` URL
2. Check the response shows admin credentials
3. Use exact email: `admin@bloodchai.org`
4. Use exact password: `admin123`

### "Database connection error"
1. Verify DATABASE_URL in Vercel environment variables
2. Make sure Supabase project is not paused
3. Check if IP restrictions are disabled in Supabase

### "Build fails on Vercel"
1. Check build logs in Vercel dashboard
2. Ensure all environment variables are set
3. Try redeploying after fixing issues

---

## 📞 Support

For issues, check the browser console for errors or Vercel deployment logs.
