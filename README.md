# 📚 Department Assignment Portal

A clean, real-time web portal where **faculty can post assignments** and **students can browse & download them** — no student login required.

---

## ✨ Features

### 👨‍🎓 Student View (Public — No Login Needed)
- Opens directly to the assignment list
- Filter by **subject**, search by title, sort by due date or newest
- Download assignment files with one click
- Stats: Total assignments · Due this week · Overdue · Subject count

### 👨‍🏫 Faculty Dashboard (Login Required)
- Register / Login as faculty
- Post assignments with title, subject, due date, file upload, and notes
- View all posted assignments with status badges
- Delete assignments
- Real-time updates — changes appear instantly

---

## 🖥️ Screenshots

> Student View — public, no login needed

![Student View](https://via.placeholder.com/900x450/F7F8FA/1C2333?text=Student+Assignment+List)

> Faculty Dashboard — post and manage assignments

![Faculty Dashboard](https://via.placeholder.com/900x450/F7F8FA/1C2333?text=Faculty+Dashboard)

---

## 🧱 Tech Stack

| Layer | Technology |
|---|---|
| Frontend | React 19 + Vite 7 |
| Language | TypeScript |
| Database | Firebase Realtime Database |
| File Storage | Cloudinary (unsigned upload) |
| Fonts | IBM Plex Sans / Serif / Mono |
| Hosting | Any static host (Vercel, Netlify, etc.) |

---

## 📁 Project Structure

```
assignment-portal/
├── src/
│   ├── App.tsx                    # Main router (student / faculty-auth / faculty-app)
│   ├── lib/
│   │   └── firebase.ts            # Firebase config & database instance
│   ├── types.ts                   # Shared types, SUBJECTS list, Cloudinary config
│   ├── pages/
│   │   ├── StudentView.tsx        # Public student view
│   │   └── FacultyDashboard.tsx   # Faculty dashboard
│   └── components/
│       └── AuthScreen.tsx         # Faculty login / register screen
├── public/
│   └── portal.html                # ⭐ Standalone single-file version (no build needed)
└── index.html
```

---

## 🚀 Getting Started

### Option A — Use the standalone HTML file *(Easiest)*

1. Download `public/portal.html`
2. Open it in any browser — or upload it to any web server
3. Done. No build, no npm, no setup.

### Option B — Run with Node.js (React + Vite)

**Prerequisites:** Node.js 18+, pnpm

```bash
# Clone the repo
git clone https://github.com/your-username/assignment-portal.git
cd assignment-portal

# Install dependencies
pnpm install

# Start development server
pnpm dev
```

Open [http://localhost:5173](http://localhost:5173)

---

## 🔧 Configuration

### Firebase Setup
1. Go to [Firebase Console](https://console.firebase.google.com/) → Create a project
2. Enable **Realtime Database** → Start in **test mode**
3. Copy your config into `src/lib/firebase.ts`:

```ts
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  databaseURL: "https://YOUR_PROJECT-default-rtdb.firebaseio.com",
  projectId: "YOUR_PROJECT",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

> ⚠️ **Firebase Rules:** Make sure your Realtime Database rules allow read/write.  
> For a classroom setup, test mode rules work fine. For production, lock down write rules.

### Cloudinary Setup
1. Create a free account at [cloudinary.com](https://cloudinary.com)
2. Go to **Settings → Upload → Upload presets**
3. Create an **unsigned** preset (e.g., `assignment_uploads`)
4. Allow all file types (raw) for PDF, DOCX, etc.
5. Update `src/types.ts`:

```ts
export const CLOUDINARY_CLOUD_NAME = "your_cloud_name";
export const CLOUDINARY_UPLOAD_PRESET = "assignment_uploads";
```

---

## 📚 Subjects

The portal is pre-configured with 6 subjects:

| # | Subject |
|---|---|
| 1 | Java Programming |
| 2 | Python |
| 3 | ERP (Enterprise Resource Planning) |
| 4 | NGD (Next Generation Database) |
| 5 | Software Testing |
| 6 | Cyber Security |

To change subjects, edit the `SUBJECTS` array in `src/types.ts`.

---

## 🗄️ Firebase Data Structure

```
firebase-root/
├── users/
│   └── faculty/
│       └── {username}/
│           ├── name: "Prof. Sharma"
│           ├── username: "sharma"
│           ├── password: "****"      ← plaintext (classroom use only)
│           └── role: "faculty"
└── assignments/
    └── {auto-id}/
        ├── title: "Unit 3 Problem Set"
        ├── subject: "Java Programming"
        ├── due: "2025-07-15"
        ├── notes: "Refer chapter 5"
        ├── fileUrl: "https://res.cloudinary.com/..."
        ├── fileName: "assignment3.pdf"
        ├── postedBy: "Prof. Sharma"
        ├── postedByUsername: "sharma"
        └── createdAt: 1718000000000
```

---

## ⚙️ Build for Production

```bash
pnpm build
# Output in dist/ — deploy to any static host
```

**Deploy options:**
- [Vercel](https://vercel.com) — `vercel deploy`
- [Netlify](https://netlify.com) — drag & drop `dist/`
- [GitHub Pages](https://pages.github.com)
- Any web server — just copy `dist/` files

---

## 🔒 Security Note

> This project stores faculty passwords in **plaintext** in Firebase.  
> It is designed for **classroom / internal use only**.  
> Do **not** use this for sensitive or production environments without adding proper auth (e.g., Firebase Authentication).

---

## 📄 License

MIT — free to use, modify, and distribute.

---

## 🙌 Credits

Built with ❤️ using React, Firebase, and Cloudinary.  
Typography: [IBM Plex](https://www.ibm.com/plex/) by IBM.
