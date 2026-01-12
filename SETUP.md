# SnapMap Setup

Before you start, you'll need:
- Node.js v16+
- npm
- An Azure account (free credits with GitHub Student Pack)
- A Clerk account

## Azure Setup

1. Go to https://portal.azure.com and create a storage account
2. Inside that, create a container called `snapmap-images`
3. Set the container's access level to "Blob" (so images are publicly readable)
4. Go to Access keys and copy the connection string

## Clerk Setup

1. Create an app at https://clerk.com
2. Grab your publishable key (frontend) and secret key (backend) from the dashboard

## Backend

Create `backend/.env`:
```
PORT=5000
MONGODB_URI=your_mongo_uri
AZURE_STORAGE_CONNECTION_STRING=paste_your_connection_string
AZURE_BLOB_CONTAINER=snapmap-images
CLERK_SECRET_KEY=your_secret_key
```

Then:
```
cd backend
npm install
npm run dev
```

Should see "Server running on port 5000" if everything's good. Hit http://localhost:5000 to check.

## Frontend

Create `frontend/.env`:
```
EXPO_PUBLIC_CLERK_PUBLISHABLE_KEY=your_publishable_key
EXPO_PUBLIC_API_BASE_URL=http://YOUR_LOCAL_IP:5000
```

Replace YOUR_LOCAL_IP with your actual IP (run `ipconfig` on Windows or `ifconfig` on Mac/Linux).

Then:
```
cd frontend
npm install
npx expo start
```

Scan the QR with Expo Go on your phone. Make sure phone and laptop are on same wifi.

## Notes

- Don't commit .env files
- Azure container needs to be public
- Your phone needs to reach your laptop's IP for the app to work
